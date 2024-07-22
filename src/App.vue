<script setup>
import Header from './components/HeaderComponent.vue'
import Drawer from './components/DrawerComponent.vue'
import CardList from './components/CardList.vue'
import axios from 'axios'
import { onMounted, ref, watch, reactive, provide } from 'vue'

const items = ref([])
const isOpenDrawer = ref(false)

const targetDrawer = () => {
  isOpenDrawer.value = !isOpenDrawer.value
}

provide('targetDrawer', targetDrawer)

const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = {
        sneakerId: item.id
      }
      const { data } = await axios.post(`https://269b3b45e08bcd1a.mokky.dev/favorites`, obj)
      console.log(data)
      item.isFavorite = true
    } else {
      await axios.delete(`https://269b3b45e08bcd1a.mokky.dev/favorites/${item.favoriteId}`)
      item.isFavorite = false
    }
  } catch (error) {
    console.log(error)
  }
}

const filters = reactive({
  sortBy: 'id',
  searchBy: ''
})

const fetchItems = async () => {
  const params = {
    sortBy: filters.sortBy
  }
  if (filters.searchBy) {
    params.title = filters.searchBy
  }
  const { data } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/items`, {
    params
  })
  items.value = data.map((sneaker) => ({
    ...sneaker,
    isFavorite: false,
    isAdded: false
  }))
}

const fetchFavorites = async () => {
  const { data: favourites } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/favorites`)
  items.value = items.value.map((item) => {
    const favourite = favourites.find((fav) => item.id === fav.sneakerId)
    if (favourite) {
      return { ...item, isFavorite: true, favoriteId: favourite.id }
    }
    return item
  })
  console.log(items.value)
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})

watch(filters, fetchItems)

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}
const onChangeInput = (event) => {
  filters.searchBy = `*${event.target.value}*`
}
</script>

<template>
  <Drawer :targetDrawer="targetDrawer" v-if="isOpenDrawer" />
  <div class="bg-white m-20 shadow-xl rounded-xl">
    <Header :targetDrawer="targetDrawer" />
    <div class="flex justify-between items-center mb-10 p-10">
      <div>
        <h1 class="text-3xl font-bold">Все кроссовки</h1>
      </div>

      <div class="flex items-center gap-4">
        <select
          @change="onChangeSelect"
          class="py-2 px-3 border border-gray-200 focus:border-gray-400 rounded-md focus:outline-none"
        >
          <option value="title">По названию</option>
          <option value="price">По цене (дешевые)</option>
          <option value="-price">По цене (дорогие)</option>
        </select>
        <div class="relative">
          <input
            @input="onChangeInput"
            type="text"
            class="border border-gray-200 rounded-md py-2 pl-10 pr-4 focus:outline-none focus:border-gray-400"
            placeholder="Поиск..."
          />
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <img src="/search.svg" />
          </div>
        </div>
      </div>
    </div>

    <CardList :items="items" @addToFavorite="addToFavorite" />
  </div>
</template>

<style scoped>
</style>