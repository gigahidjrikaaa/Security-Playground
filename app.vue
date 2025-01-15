<script setup lang="ts">
const version = 2 + 1
</script>

<template>
  <div class="flex h-screen">
    <aside class="w-64 bg-gray-800 text-white p-4">
      <ul>
        <li class="mb-4"><NuxtLink to="/" class="hover:text-gray-400">Home</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/profile" class="hover:text-gray-400">Profile</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/settings" class="hover:text-gray-400">Settings</NuxtLink></li>
        <li class="mb-4"><NuxtLink to="/signin" class="hover:text-gray-400">Sign In</NuxtLink></li>
      </ul>
    </aside>
    <main class="flex-1 p-8">
      <NuxtPage />
    </main>
  </div>
</template>