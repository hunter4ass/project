<script setup>
import { inject } from 'vue'
const { closeSign } = inject('signActions')
const emit = defineEmits(['openRegister'])
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-60"></div>
  <div
    v-auto-animate
    class="bg-white w-1/4 h-1/3 fixed top-1/4 right-0 left-0 bottom-0 mx-auto z-20 p-7 border rounded-2xl"
  >
    <form class="">
      <svg
        @click="closeSign"
        class="float-right opacity-30 cursor-pointer hover:opacity-100"
        width="32"
        height="32"
        viewBox="0 0 16 16"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M4.11 2.697L2.698 4.11 6.586 8l-3.89 3.89 1.415 1.413L8 9.414l3.89 3.89 1.413-1.415L9.414 8l3.89-3.89-1.415-1.413L8 6.586l-3.89-3.89z"
          fill="#000"
        ></path>
      </svg>
      <h1 class="text-3xl font-bold mb-4">Вход в ваш аккаунт</h1>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="email">Почта</label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="email"
          type="email"
          placeholder="qweasd123@mail.ru"
        />
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="password">Пароль</label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="password"
          type="password"
          placeholder="********"
        />
      </div>
      <div class="flex items-center justify-between">
        <button
          class="bg-orange-500 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded"
          type="submit"
        >
          Войти
        </button>
        <a
          @click="
            () => {
              closeSign()
              emit('openRegister')
            }
          "
          class="float-right bg-green-500 hover:bg-green-700 text-white font-bold py-1 px-2 mt-2 roundedd cursor-pointer"
          type=""
        >
          Зарегестрироваться
        </a>
      </div>
    </form>
  </div>
</template>
