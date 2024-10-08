<script setup>
defineProps({
  title: String,
  description: String,
  imageUrl: String
})
</script>
<template>
  <div class="flex flex-col items-center text-center w-80 mx-auto" v-auto-animate>
    <img class="h-16 w-16" :src="imageUrl" alt="" />
    <h2 class="mt-4 text-2xl font-medium">{{ title }}</h2>
    <p class="text-slate-500 mt-1">{{ description }}</p>
  </div>
</template>
