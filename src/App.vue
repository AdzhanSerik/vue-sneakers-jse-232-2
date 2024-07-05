<script setup>
import Header from './components/HeaderComponent.vue'
import Sneaker from './components/SneakerSingle.vue'
</script>

<template>
  <div class="bg-white m-20 shadow-xl rounded-xl">
    <Header />
    <h2 class="p-10 text-2xl font-bold">Все кроссовки</h2>
    <div class="p-10 grid grid-cols-4 gap-5">
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
      <Sneaker />
    </div>
  </div>
</template>

<style scoped>
</style>