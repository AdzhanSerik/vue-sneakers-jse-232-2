<template>
  <Loader v-if="isLoading" />
  <CardList :items="items" />
  <EmptyFavorites v-if="!isLoading && !items.length" />
</template>

<script setup>
import CardList from '../components/CardList.vue'
import EmptyFavorites from '../components/EmptyFavorites.vue'
import Loader from '../components/LoaderComponent.vue'
import axios from 'axios'
import { onMounted, ref } from 'vue'

const items = ref([])
const isLoading = ref(true)

const fetchItems = async () => {
  const { data } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/items`)
  const datas = data
  const { data: favorites } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/favorites`)
  items.value = datas.filter((item) => {
    return favorites.some((fav) => item.id === fav.sneakerId)
  })

  isLoading.value = false
  items.value = items.value.map((item) => ({
    ...item,
    isFavorite: true
  }))
}

onMounted(async () => {
  await fetchItems()
})
</script>

