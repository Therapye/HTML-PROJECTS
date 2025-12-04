<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="min-h-screen bg-white dark:bg-gray-900">
    <header>
      <div class="max-w-4xl mx-auto">
        <nav class="p-4 bg-gray-100 dark:bg-gray-800 rounded-b-lg shadow-md flex gap-4">
          <RouterLink to="/" class="text-blue-600 hover:text-blue-800 font-medium dark:text-blue-400">Home</RouterLink>
          <RouterLink to="/about" class="text-blue-600 hover:text-blue-800 font-medium dark:text-blue-400">About</RouterLink>
          <RouterLink to="/contact" class="text-blue-600 hover:text-blue-800 font-medium dark:text-blue-400">Contact</RouterLink>
        </nav>
      </div>
    </header>

    <main class="max-w-4xl mx-auto mt-5">
      <RouterView />
    </main>
  </div>
</template>