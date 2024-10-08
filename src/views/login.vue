<template>
  <div class="flex justify-center items-center h-screen">
    <form @submit.prevent="login" class="bg-white p-6 rounded shadow-md w-80">
      <h2 class="mb-4 text-2xl">Вход</h2>
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
      <button type="submit" class="bg-blue-500 text-white p-2 w-full">Войти</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async login() {
      try {
        const response = await axios.post('https://your-api-url.com/login', {
          email: this.email,
          password: this.password
        })
        // Сохраните токен или выполните редирект
        console.log(response.data)
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>
