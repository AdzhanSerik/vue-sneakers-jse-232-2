<template>
  <CardList :items="items" />
</template>

<script setup>
import CardList from '../components/CardList.vue'
import axios from 'axios'
import { onMounted, ref } from 'vue'

const items = ref([])

const fetchItems = async () => {
  const { data } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/items`)
  items.value = data
}

const fetchFavorites = async () => {
  const { data: favorites } = await axios.get(`https://269b3b45e08bcd1a.mokky.dev/favorites`)
  items.value = items.value.filter((item) => {
    return favorites.some((fav) => item.id === fav.sneakerId)
  })

  items.value = items.value.map((item) => ({
    ...item,
    isFavorite: true
  }))
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
</script>

