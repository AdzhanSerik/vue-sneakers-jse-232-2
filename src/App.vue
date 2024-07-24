<script setup>
import Header from './components/HeaderComponent.vue'
import Drawer from './components/DrawerComponent.vue'
import Home from './pages/HomeComponent.vue'

import { ref, provide } from 'vue'

const isOpenDrawer = ref(false)
const targetDrawer = () => {
  isOpenDrawer.value = !isOpenDrawer.value
}
provide('targetDrawer', targetDrawer)
</script>

<template>
  <Drawer :targetDrawer="targetDrawer" v-if="isOpenDrawer" />
  <div class="bg-white m-20 shadow-xl rounded-xl">
    <Header :targetDrawer="targetDrawer" />
    <div class="p-10">
      <Home />
    </div>
  </div>
</template>

<style scoped>
</style>