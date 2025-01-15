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
        </form>
        <p v-if="errorMessage" class="mt-4 text-red-500 text-center">{{ errorMessage }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        errorMessage: ''
      };
    },
    methods: {
      handleSubmit() {
        // Simulate sign-in logic
        if (this.username === 'admin' && this.password === 'admin') {
          alert('Sign in successful!');
          // Redirect to another page or perform other actions
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