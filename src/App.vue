<script setup>
import Header from './components/HeaderComponent.vue'
// import Drawer from './components/DrawerComponent.vue'
import CardList from './components/CardList.vue'
import axios from 'axios'
import { onMounted, ref } from 'vue'

const items = ref([])

onMounted(async () => {
  const { data } = await axios.get('https://269b3b45e08bcd1a.mokky.dev/items')
  items.value = data
})
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white m-20 shadow-xl rounded-xl">
    <Header />
    <h2 class="p-10 text-2xl font-bold">Все кроссовки</h2>
    <CardList :items="items" />
  </div>
</template>

<style scoped>
</style>