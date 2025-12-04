<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import logoImg from '@/assets/logo-heart.png'

const router = useRouter()


const username = ref('')
const password = ref('')
const errors = ref({ username: '', password: '' })

const handleLogin = () => {
  errors.value = { username: '', password: '' }
  let isValid = true

  if (!username.value.trim()) {
    errors.value.username = 'Username is required'
    isValid = false
  }
  if (!password.value) {
    errors.value.password = 'Password is required'
    isValid = false
  }

  if (isValid) {
    console.log('Login Form Data:', {
      username: username.value,
      password: password.value
    })
    alert('Login successful! Check console.')
  }
}

const goToRegister = () => router.push('/register')
</script>

<template>
  <div class="bg-gray-200 py-10 min-h-screen flex justify-center items-center font-sans">
    
    <section class="w-[375px] h-[812px] bg-[#FF5F5F] rounded-[30px] border-2 border-black 
                    flex flex-col items-center overflow-hidden pt-[100px] pb-10 shadow-xl">

      <img 
        class="w-[120px] mb-2 object-contain"
        :src="logoImg"
        alt="Fated Logo"
      >

      <h1 class="text-white text-[40px] mb-[80px] font-cursive">
        FATED
      </h1>

      <div class="flex gap-3 mb-6">
        <div class="w-[130px] py-2 rounded text-center font-bold text-[14px] bg-white text-[#ff5c5c] cursor-default shadow-md">
          LOGIN
        </div>
        <div @click="goToRegister" class="w-[130px] py-2 rounded text-center font-bold text-[14px] bg-[#ff7f7f] text-white cursor-pointer hover:bg-[#ff6b6b] transition">
          REGISTER
        </div>
      </div>

      <form @submit.prevent="handleLogin" class="flex flex-col items-center w-full gap-4">

        <div class="w-[82%] relative">
          <input 
            v-model="username"
            type="text" 
            placeholder="user name"
            class="w-full bg-white py-4 rounded text-center font-semibold text-[15px] text-gray-600 outline-none focus:ring-2 focus:ring-yellow-300 placeholder-gray-400"
            :class="{'border-2 border-red-800': errors.username}"
          />
          <span v-if="errors.username" class="text-white text-xs absolute -bottom-4 left-0">{{ errors.username }}</span>
        </div>

        <div class="w-[82%] relative">
          <input 
            v-model="password"
            type="password" 
            placeholder="password"
            class="w-full bg-white py-4 rounded text-center font-semibold text-[15px] text-gray-600 outline-none focus:ring-2 focus:ring-yellow-300 placeholder-gray-400"
            :class="{'border-2 border-red-800': errors.password}"
          />
          <span v-if="errors.password" class="text-white text-xs absolute -bottom-4 left-0">{{ errors.password }}</span>
        </div>

        <div class="w-[82%] text-right text-white text-[12px] cursor-pointer hover:underline">
          FORGOT PASSWORD?
        </div>

        <button type="submit" class="w-[82%] bg-white text-[#ff5c5c] py-4 rounded text-center font-extrabold text-[16px] mt-6 hover:bg-gray-100 transition shadow-lg">
          LOGIN
        </button>

      </form>

      <div class="text-white text-[12px] mt-6">
        DON'T HAVE AN ACCOUNT? <span @click="goToRegister" class="font-bold cursor-pointer hover:underline">REGISTER</span>
      </div>

    </section>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cherry+Bomb+One&display=swap');
.font-cursive {
  font-family: 'Cherry Bomb One', cursive;
}
</style>