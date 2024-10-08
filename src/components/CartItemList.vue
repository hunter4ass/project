<script setup>
import { inject } from 'vue'
const { cart, removeFromCart } = inject('cart')
</script>
<template>
  <div
    v-auto-animate
    class="flex items-center border borde-slate-100 p-4 rounded-xl gap-4 mb-5"
    v-for="(item, index) in cart"
    :key="index"
  >
    <img class="w-16 h-16" :src="'http://lifestealer86.ru/' + item.image" alt="" />
    <div class="flex flex-col" v-auto-animate>
      <p>{{ item.name }}</p>
      <div class="flex justify-between mt-2" v-auto-animate>
        <b>{{ item.price }}руб</b>
        <img
          src="/close.png"
          alt=""
          class="ml-auto opacity-20 hover:opacity-100 cursor-pointer transition"
          @click="removeFromCart(item)"
        />
      </div>
    </div>
  </div>
</template>
