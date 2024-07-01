<script setup>
import Sneakers from './components/SneakersCart.vue'
</script>

<template>
  <!-- <MyHello /> -->
  <div class="carts">
    <Sneakers name="Кеды" brand="Nike" :price="25000" />
    <Sneakers name="Сапоги" brand="Adidas" :price="70000" />
    <Sneakers name="Сапоги" brand="Adidas" :price="70000" />
    <Sneakers name="Сапоги" brand="Adidas" :price="70000" />
    <Sneakers name="Сапоги" brand="Adidas" :price="70000" />
    <Sneakers name="Сапоги" brand="Adidas" :price="70000" />
  </div>
</template>

<style scoped>
h1 {
  font-size: 30px;
  text-align: center;
}
.carts {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}
</style>