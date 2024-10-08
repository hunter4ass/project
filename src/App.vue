<script setup>
import axios from 'axios'
import { onMounted, ref, reactive, provide, watch, computed } from 'vue'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'
import register from './components/register.vue'
import sign from './components/sign.vue'
const drawerOpen = ref(false)
const registerOpen = ref(false)
const signOpen = ref(false)
const totalPrice = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0).toFixed(1))
const createOrder = async () => {
  try {
    const { data } = await axios.post('http://lifestealer86.ru/api-shop/order/', {
      items: cart.value,
      totalPrice: totalPrice.value
    })

    cart.value = []
    return data
  } catch (error) {
    console.log(error)
  }
}
const cart = ref([])
const closeSign = () => {
  signOpen.value = false
}
const openSign = () => {
  signOpen.value = true
}
const closeRegister = () => {
  registerOpen.value = false
}
const openRegister = () => {
  registerOpen.value = true
}
const closeDrawer = () => {
  drawerOpen.value = false
}
const openDrawer = () => {
  drawerOpen.value = true
}
const addToCart = (item) => {
  cart.value.push(item)
  item.isAdded = true
  axios
    .post('http://lifestealer86.ru/api-shop/cart/', {
      itemId: item.id,
      quantity: 1
    })
    .then((response) => console.log(response.data))
    .catch((error) => console.error(error))
}
const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false
}

const onClickAddPlus = (item) => {
  if (!item.isAdded) {
    addToCart(item)
  } else {
    removeFromCart(item)
  }
}
provide('cart', {
  cart,
  closeDrawer,
  openDrawer,
  addToCart,
  removeFromCart
})
provide('registerActions', {
  closeRegister,
  openRegister
})
provide('signActions', {
  closeSign,
  openSign
})
</script>

<template>
  <modal />
  <sign v-if="signOpen" @open-register="openRegister" />
  <register v-if="registerOpen" @open-sign="openSign" />
  <drawer v-if="drawerOpen" :total-price="totalPrice" @create-order="createOrder" />
  <div class="bg-white w-3/5 m-auto rounded-xl shadow-xl mt-14">
    <Header :total-price="totalPrice" @open-register="openRegister" @open-drawer="openDrawer" />
    <div class="p-10">
      <h2 class="text-3xl font-bold mb-10">Все продукты</h2>
      <CardList :items="items" @add-to-cart="onClickAddPlus" />
    </div>
  </div>
</template>
