<script setup>
const props = defineProps({
  title: String,
  price: Number
})
console.log(props)
</script>

<template>
  <div class="product">
    <h2>Товар {{ title }}</h2>
    <h3>цена : {{ price }}</h3>
    <slot></slot>
  </div>
</template>

<style scoped>
.product {
  border: 1px solid red;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
