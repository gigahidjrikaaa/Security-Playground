<template>
    <div>
      <h1 class="text-3xl font-bold">Settings Page</h1>
      <div v-if="isAuthenticated">
        <h2 class="text-2xl font-bold mt-4">Account Settings</h2>
        <p>Manage your account settings here.</p>
        <!-- Add account settings form or content here -->
  
        <h2 class="text-2xl font-bold mt-4">General Settings</h2>
        <p>Manage your general settings here.</p>
        <!-- Add general settings form or content here -->
      </div>
      <div v-else>
        <p>You are not logged in. Redirecting to the sign-in page...</p>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue'
  import { useRouter } from 'vue-router'
  
  export default {
    setup() {
      const isAuthenticated = ref(false)
      const router = useRouter()
  
      onMounted(() => {
        // Check authentication state
        isAuthenticated.value = localStorage.getItem('isAuthenticated') === 'true';
        if (!isAuthenticated.value) {
          setTimeout(() => {
            router.push('/profile/signin')
          }, 2000) // Redirect after 2 seconds
        }
      })
  
      return {
        isAuthenticated
      }
    }
  }
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>