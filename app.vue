<script setup lang="ts">
const version = 2 + 1
</script>

<template>
  <div class="flex h-screen w-screen">
    <aside class="w-64 bg-gray-800 text-white">
      <ul>
        <li class="mb-4"><a href="#" class="hover:text-gray-400">Home</a></li>
        <li class="mb-4"><a href="#" class="hover:text-gray-400">Profile</a></li>
        <li class="mb-4"><a href="#" class="hover:text-gray-400">Settings</a></li>
        <li class="mb-4"><a href="#" class="hover:text-gray-400">Logout</a></li>
      </ul>
    </aside>
    <main class="flex-1 p-8">
      <div class="text-3xl font-bold">
        Hello Nuxt {{ version }}!
      </div>
    </main>
  </div>
</template>

<style scoped>
</style>