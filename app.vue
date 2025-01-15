<script setup lang="ts">
import { ref } from 'vue'

const version = '1.0.0'
const isSidebarOpen = ref(true)

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}
</script>

<template>
  <div class="flex h-screen">
    <aside :class="{'-translate-x-full': !isSidebarOpen, 'translate-x-0': isSidebarOpen}" class="relative w-64 bg-gray-800 text-white py-4 transform transition-transform duration-300 ease-in-out">
      <button @click="toggleSidebar" class="absolute top-4 right-[-1.5rem] z-10 bg-gray-800 text-white p-2 rounded-lg">
        <span v-if="isSidebarOpen">←</span>
        <span v-else>→</span>
      </button>
      <h1 class="text-3xl font-bold text-center font-mono">Security Playground</h1>
      <p class="text-center">Version {{ version }}</p>
      <p class="text-center italic text-sm text-gray-400">developed by <a href="https://www.linkedin.com/in/gigahidjrikaaa" target="_blank" class="underline">gigahidjrikaaa</a></p>
      <hr class="my-4 border-gray-700" />
      <ul v-if="isSidebarOpen" class="mt-4">
        <li class="mb-0 bg-gray-700 rounded"><NuxtLink to="/" class="block p-4 hover:bg-gray-600" active-class="bg-green-500 hover:bg-green-400">Home</NuxtLink></li>
        <li class="mb-0 bg-gray-700 rounded"><NuxtLink to="/profile" class="block p-4 hover:bg-gray-600" active-class="bg-green-500 hover:bg-green-400">Profile</NuxtLink></li>
        <li class="mb-0 bg-gray-700 rounded"><NuxtLink to="/settings" class="block p-4 hover:bg-gray-600" active-class="bg-green-500 hover:bg-green-400">Settings</NuxtLink></li>
        <li class="mb-0 bg-gray-700 rounded"><NuxtLink to="/signin" class="block p-4 hover:bg-gray-600" active-class="bg-green-500 hover:bg-green-400">Sign In</NuxtLink></li>
      </ul>
      <hr class="my-4 border-gray-700" />
      <p class="absolute bottom-4 text-center w-full text-gray-400">Vite + Vue 3 + Tailwind CSS</p>
    </aside>
    <main :class="{'ml-4': isSidebarOpen, '-ml-60': !isSidebarOpen}" class="flex-1 p-8 transition-all duration-300 ease-in-out">
      <NuxtPage />
    </main>
  </div>
</template>

<style scoped>
/* No additional styles needed as Tailwind CSS is being used */
</style>