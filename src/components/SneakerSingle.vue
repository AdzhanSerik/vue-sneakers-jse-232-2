<script setup>
defineProps({
  title: String,
  id: Number,
  image: String,
  price: Number,
  isAdded: Boolean,
  isFavorite: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>

<template>
  <div
    class="border p-8 border-slate-200 rounded-3xl relative cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
  >
    <img
      @click="onClickFavorite(id)"
      class="absolute top-4 left-4"
      :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
      alt="Like"
    />
    <img class="w-52 h-52 object-contain" :src="image" alt="Sneaker" />
    <p>{{ title }}</p>
    <div class="flex justify-between items-center">
      <div class="flex flex-col">
        <span class="text-slate-400">Цена:</span>
        <span class="font-bold">{{ price }} тенге</span>
      </div>
      <img @click="onClickAdd" :src="isAdded ? '/checked.svg' : '/plus.svg'" alt="" />
    </div>
  </div>
</template>