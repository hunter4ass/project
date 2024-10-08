<script setup>
import card from './card.vue'
defineProps({
  items: Array
})

const emit = defineEmits(['addToCart'])
</script>
<template>
  <div class="grid grid-cols-4 gap-5" v-auto-animate>
    <card :onClickAdd="(item) => emit('addToCart', item)" :items="items" />
  </div>
</template>
