<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-50"></div>
  <div class="fixed top-0 right-0 h-full w-96 bg-white z-20 p-8 overflow-auto">
    <Header />
    <div class="flex flex-col h-full mt-5">
      <div class="flex flex-col gap-5">
        <CartItem />
        <CartItem />
        <CartItem />
        <CartItem />
        <CartItem />
        <CartItem />
      </div>

      <div>
        <div class="flex flex-col gap-5">
          <div class="flex items-end gap-2">
            <span>Итого:</span>
            <div class="flex-1 border-b border-dashed" />
            <span class="font-bold">1000 руб.</span>
          </div>

          <div class="flex items-end gap-2">
            <span>Налог 5%:</span>
            <div class="flex-1 border-b border-dashed" />
            <span class="font-bold">50 руб.</span>
          </div>
        </div>

        <button
          class="flex justify-center items-center gap-3 w-full py-3 mt-10 mb-5 bg-lime-500 text-white rounded-xl transition active:bg-lime-700 hover:bg-lime-600"
        >
          Оформить заказ
          <img src="/arrow-next.svg" alt="Arrow" />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import Header from './HeaderCart.vue'
import CartItem from './CartItem.vue'
</script>
