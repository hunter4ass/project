<script setup>
defineProps({
  totalPrice: Number
})
const emit = defineEmits(['openDrawer'])
</script>

<template>
  <header class="flex justify-between border-b border-slate-300 px-10 py-8" v-auto-animate>
    <div class="flex items-center gap-4">
      <img src="/favicon.ico" alt="logo" class="" />
      <div>
        <h2 class="text-xl font-bold uppercase">VUE-BIKE</h2>
      </div>
    </div>

    <ul class="flex items-center gap-10">
      <li
        @click="() => emit('openDrawer')"
        class="flex items-center cursor-pointer gap-3 text-gray-600 hover:text-black"
      >
        <img src="/add-to-cart-icon.png" alt="cart" />
        <b>{{ totalPrice }} руб</b>
      </li>
      <li class="flex items-center cursor-pointer gap-3 text-gray-600 hover:text-black">
        <img src="/heart-thin-icon.png" alt="cart" />
        <b>Закладки</b>
      </li>
      <li
        @click="() => emit('openRegister')"
        class="flex items-center cursor-pointer gap-3 text-gray-600 hover:text-black"
      >
        <img src="/profile-boy-icon.png" alt="cart" />
        <b>Профиль</b>
      </li>
    </ul>
  </header>
</template>
