<script setup>
import Sneaker from './SneakerSingle.vue'

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Добавлено нахой!')
}
</script>

<template>
  <div class="p-10 grid grid-cols-4 gap-5">
    <Sneaker
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :image="item.imageUrl"
      :price="item.price"
      :isAdded="true"
      :isFavourite="true"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>