<template>
  <div class="flex justify-center items-center h-screen">
    <form @submit.prevent="register" class="bg-white p-6 rounded shadow-md w-80">
      <h2 class="mb-4 text-2xl">Регистрация</h2>
      <input type="text" v-model="name" placeholder="Имя" class="border p-2 w-full mb-4" required />
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
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
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
        const response = await axios.post('https://your-api-url.com/register', {
          name: this.name,
          email: this.email,
          password: this.password
        })
        // Обработка успешной регистрации
        console.log(response.data)
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>
