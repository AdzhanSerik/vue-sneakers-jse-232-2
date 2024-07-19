<script setup>
import Sneaker from './SneakerSingle.vue'
import { inject } from 'vue'

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Добавлено нахой!')
}

const addToFavorite = inject('addToFavorite')
const onClickFavorite = (id) => {
  addToFavorite(id)

  alert(id)
}
</script>


<template>
  <div class="p-10 grid grid-cols-4 gap-5">
    <Sneaker
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :image="item.imageUrl"
      :price="item.price"
      :isAdded="item.isAdded"
      :isFavourite="item.isFavourite"
      :onClickAdd="onClickAdd"
      :onClickFavorite="onClickFavorite"
    />
  </div>
</template>