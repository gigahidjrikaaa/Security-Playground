<template>
  <div class="flex items-center justify-center h-full bg-gray-100">
    <div class="bg-white p-8 rounded shadow-md w-full max-w-md">
      <h1 class="text-3xl font-bold mb-4 text-center font-mono">Security Playground</h1>
      <hr class="my-4 border-gray-300" />
      <h1 class="text-3xl font-bold mb-4 text-center">Sign In</h1>
      <form @submit.prevent="handleSubmit">
        <div class="mb-4">
          <label for="username" class="block text-sm font-medium text-gray-700">Username</label>
          <input v-model="username" type="text" id="username" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your username" />
        </div>
        <div class="mb-4">
          <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
          <input v-model="password" type="password" id="password" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your password" />
        </div>
        <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full">Sign In</button>
        <p class="mt-4 text-center">Don't have an account?
          <button type="button" @click="showModal" class="text-blue-500">Sign up</button>
        </p>
      </form>
      <p v-if="errorMessage" class="mt-4 text-red-500 text-center">{{ errorMessage }}</p>
    </div>
    <div v-if="isModalVisible" class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50">
      <div class="bg-white p-8 rounded shadow-md w-full max-w-md">
        <h3 class="text-xl font-bold mb-4">Notice</h3>
        <p>Contact administrator for account creation</p>
        <button @click="isModalVisible = false" class="mt-4 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'

export default {
  data() {
    return {
      username: '',
      password: '',
      errorMessage: '',
      isModalVisible: false
    };
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    handleSubmit() {
      // Simulate sign-in logic
      if (this.username === 'admin' && this.password === 'admin') {
        // Store a flag in local storage to indicate the user is logged in
        localStorage.setItem('isAuthenticated', 'true');
        alert('Sign in successful!');
        // Redirect to the settings page
        this.$router.push('/profile/settings');
      } else {
        this.errorMessage = 'Invalid username or password';
      }
    }
  }
};
</script>

<style scoped>
/* No additional styles needed as Tailwind CSS is being used */
</style>