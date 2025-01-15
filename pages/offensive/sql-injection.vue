<template>
    <div class="p-8">
      <h1 class="text-3xl font-bold mb-4">SQL Injection Playground</h1>
      <p class="mb-4">
        SQL Injection is a code injection technique that exploits a security vulnerability in an application's software by manipulating SQL queries. This playground demonstrates how SQL injection can be used to bypass authentication.
      </p>
      <form @submit.prevent="handleLogin">
        <div class="mb-4">
          <label for="username" class="block text-sm font-medium text-gray-700">Username</label>
          <input v-model="username" type="text" id="username" class="mt-1 block w-full border p-2" placeholder="Enter username" />
        </div>
        <div class="mb-4">
          <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
          <input v-model="password" type="password" id="password" class="mt-1 block w-full border p-2" placeholder="Enter password" />
        </div>
        <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Login</button>
      </form>
      <div v-if="response" class="mt-4 p-4 border rounded bg-gray-100">
        <h2 class="text-xl font-bold mb-2">Simulated Backend Response</h2>
        <pre>{{ response }}</pre>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        response: null
      };
    },
    methods: {
      handleLogin() {
        // Simulate a vulnerable SQL query
        const query = `SELECT * FROM users WHERE username = '${this.username}' AND password = '${this.password}'`;
  
        // Simulate a backend response
        if (this.username === "admin' --" || this.username === "admin' #") {
          this.response = `Query: ${query}\n\nLogin successful! Welcome, admin.`;
        } else {
          this.response = `Query: ${query}\n\nLogin failed. Invalid username or password.`;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>