<script setup>
defineProps({
  totalPrice: Number
})
import DrawerHead from './DrawerHead.vue'
import CartListItem from './CartItemList.vue'
import InfoBlock from './InfoBlock.vue'
const emit = defineEmits(['createOrder'])
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-60"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-7" v-auto-animate>
    <DrawerHead />
    <div v-if="totalPrice == 0" class="flex mt-80 items-center">
      <InfoBlock
        title="Корзина пуста."
        description="Добавьте что нибудь интересное в корзину для оформления заказа."
        image-url="/favicon.ico"
      />
    </div>
    <CartListItem />
    <div v-if="totalPrice > 0" class="mt-7 my-7">
      <div class="flex gpa-2">
        <span>Итог:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>{{ totalPrice }}руб</b>
      </div>
      <button
        :disabled="totalPrice <= 0"
        @click="() => emit('createOrder')"
        class="mt-7 bg-lime-500 w-full rounded-xl py-2 text-white hover:bg-lime-600 disabled:bg-slate-300 transition active:bg-lime-800 cursor-pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
