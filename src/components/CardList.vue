<script setup>
import Sneaker from './SneakerSingle.vue'

defineProps({
  items: Array
})

const emit = defineEmits(['addToFavorite'])

const onClickAdd = () => {
  alert('Добавлено нахой!')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5" v-auto-animate>
    <Sneaker
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :image="item.imageUrl"
      :price="item.price"
      :isAdded="item.isAdded"
      :isFavorite="item.isFavorite"
      :onClickAdd="onClickAdd"
      :onClickFavorite="() => emit('addToFavorite', item)"
    />
  </div>
</template>