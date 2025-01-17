<template>
    <div class="p-8">
      <h1 class="text-3xl font-bold mb-4">Phishing Simulation</h1>
      <p class="mb-4">
        Phishing is a type of social engineering attack often used to steal user data, including login credentials and credit card numbers. It occurs when an attacker masquerades as a trusted entity to trick a victim into opening an email, instant message, or text message.
      </p>
      <p class="mb-4">
        This simulation demonstrates how a phishing attack can capture user credentials. Enter your username and password below to see how the attack works.
      </p>
      <div class="bg-yellow-200 p-4 rounded mb-4">
        <p><strong>Note:</strong> This is a simulation. Do not enter your real credentials.</p>
      </div>
      <form @submit.prevent="handleSubmit">
        <div class="mb-4">
          <label for="username" class="block text-sm font-medium text-gray-700">Username</label>
          <input v-model="username" type="text" id="username" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your username" />
        </div>
        <div class="mb-4">
          <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
          <input v-model="password" type="password" id="password" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your password" />
        </div>
        <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Submit</button>
      </form>
      <div v-if="capturedCredentials" class="mt-4 p-4 border rounded bg-gray-100">
        <h2 class="text-xl font-bold mb-2">Captured Credentials</h2>
        <p><strong>Username:</strong> {{ capturedCredentials.username }}</p>
        <p><strong>Password:</strong> {{ capturedCredentials.password }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        capturedCredentials: null
      };
    },
    methods: {
      handleSubmit() {
        // Simulate capturing the credentials
        this.capturedCredentials = {
          username: this.username,
          password: this.password
        };
  
        // Clear the form
        this.username = '';
        this.password = '';
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>