<script>
import axios from 'axios'

export default {
  props: ['isVisible'],
  data() {
    return {
      name: '',
      email: '',
      password: ''
    }
  },
  methods: {
    async register() {
      try {
        const response = await axios.post(' http://lifestealer86.ru/api-shop/', {
          name: this.name,
          email: this.email,
          password: this.password
        })
        console.log(response.data)
        this.close()
      } catch (error) {
        console.error(error)
      }
    },
    close() {
      this.$emit('close')
    }
  }
}
</script>
<template>
  <div
    v-if="isVisible"
    class="fixed inset-0 flex justify-center items-center bg-gray-800 bg-opacity-50"
  >
    <div class="bg-white p-6 rounded shadow-md w-80">
      <h2 class="mb-4 text-2xl">Регистрация</h2>
      <form @submit.prevent="register">
        <input
          type="text"
          v-model="name"
          placeholder="Имя"
          class="border p-2 w-full mb-4"
          required
        />
        <input
          type="email"
          v-model="email"
          placeholder="Email"
          class="border p-2 w-full mb-4"
          required
        />
        <input
          type="password"
          v-model="password"
          placeholder="Пароль"
          class="border p-2 w-full mb-4"
          required
        />
        <button type="submit" class="bg-blue-500 text-white p-2 w-full">Зарегистрироваться</button>
        <button type="button" @click="close" class="mt-2 text-red-500">Закрыть</button>
      </form>
    </div>
  </div>
</template>
