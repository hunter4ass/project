<script setup>
import axios from 'axios'
import { ref } from 'vue'

const getcatalog = async () => {
  try {
    const response = await axios.get('http://lifestealer86.ru/api-shop/products')
    Array.value = response.data.data
    console.log(Array.value)
  } catch (error) {
    console.error(error)
  }
}
const Array = ref()
getcatalog()

defineProps({
  price: Number,
  title: String,
  imageUrl: String,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>
<template>
  <div
    v-auto-animate
    v-for="item in Array"
    :key="item.id"
    class="relative bg-neutral-100 border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
  >
    <img
      :src="!isFavorite ? '/like 1.png' : '/like 2.png'"
      alt="like 1"
      class="absolute top-5 left-5"
    />
    <img :src="'http://lifestealer86.ru/' + item.image" alt="bike" />
    <p>{{ item.name }}</p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цена:</span>
        <b>{{ item.price }}руб</b>
      </div>
      <div>
        <img
          :src="!item.isAdded ? '/plus.png' : '/chek.png'"
          alt="plus"
          class="mt-5"
          @click="onClickAdd(item)"
        />
      </div>
    </div>
  </div>
</template>
