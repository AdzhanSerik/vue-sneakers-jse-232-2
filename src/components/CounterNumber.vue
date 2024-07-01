<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  computed: {
    countColor() {
      return this.count < 0 ? 'red' : this.count > 0 ? 'green' : 'white'
    }
  },
  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    }
  }
}
</script>

<template>
  <div class="cart">
    <h2>Счетчик</h2>
    <h3 :style="{ color: countColor }">{{ count }}</h3>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
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
  font-size: 30px;
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
