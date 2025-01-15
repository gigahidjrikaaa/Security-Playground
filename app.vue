<script setup lang="ts">
import { ref } from 'vue'

const version = 2 + 1
const isSidebarOpen = ref(true)

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}
</script>

<template>
  <div class="flex h-screen">
    <aside :class="{'-translate-x-full': !isSidebarOpen, 'translate-x-0': isSidebarOpen}" class="relative w-64 bg-gray-800 text-white p-4 transform transition-transform duration-300 ease-in-out">
      <button @click="toggleSidebar" class="absolute top-4 right-[-1.5rem] z-10 bg-gray-800 text-white p-2 rounded-lg">
        <span v-if="isSidebarOpen">←</span>
        <span v-else>→</span>
      </button>
      <ul v-if="isSidebarOpen" class="mt-12">
        <li class="mb-4"><NuxtLink to="/" class="hover:text-gray-400">Home</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/profile" class="hover:text-gray-400">Profile</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/settings" class="hover:text-gray-400">Settings</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/signin" class="hover:text-gray-400">Sign In</NuxtLink></li>
      </ul>
    </aside>
    <main :class="{'ml-4': isSidebarOpen, '-ml-60': !isSidebarOpen}" class="flex-1 p-8 transition-all duration-300 ease-in-out">
      <NuxtPage />
    </main>
  </div>
</template>

<style scoped>
/* No additional styles needed as Tailwind CSS is being used */
</style>