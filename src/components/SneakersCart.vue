<script setup>
defineProps({
  name: String,
  brand: String,
  price: Number
})
</script>

<template>
  <div class="cart">
    <h2>{{ brand }}</h2>
    <h3>{{ name }}</h3>
    <h3>{{ `${price / 100}$` }}</h3>
    <button>Добавить в корзину</button>
  </div>
</template>

<style scoped>
.cart {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: blue;
  width: 300px;
  padding: 20px;
  border-radius: 10px;
  color: white;
}

.red {
  color: red;
}
.green {
  color: green;
}
button {
  border: none;
  outline: none;
  background: yellow;
  color: black;
  width: 100px;
  height: 50px;
  border-radius: 5px;
  font-size: 18px;
  font-weight: 700;
  transition: 0.5s;
}

h3 {
  font-size: 40px;
  color: white;
}

button:hover {
  transition: 0.5s;
  background: white;
  color: red;
}
</style>
