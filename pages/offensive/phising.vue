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
  
      <!-- Instagram Phishing Simulation -->
      <div class="flex items-center justify-center min-h-screen bg-gray-100 mb-8">
        <div class="bg-white p-8 rounded shadow-md w-full max-w-sm">
          <h1 class="text-3xl font-bold mb-4 text-center">Instagram</h1>
          <form @submit.prevent="handleSubmit">
            <div class="mb-4">
              <label for="username" class="block text-sm font-medium text-gray-700">Username</label>
              <input v-model="username" type="text" id="username" class="mt-1 block w-full border p-2 rounded" placeholder="Phone number, username, or email" />
            </div>
            <div class="mb-4">
              <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
              <input v-model="password" type="password" id="password" class="mt-1 block w-full border p-2 rounded" placeholder="Password" />
            </div>
            <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full">Log In</button>
          </form>
          <div v-if="capturedCredentials" class="mt-4 p-4 border rounded bg-gray-100">
            <h2 class="text-xl font-bold mb-2">Captured Credentials</h2>
            <p><strong>Username:</strong> {{ capturedCredentials.username }}</p>
            <p><strong>Password:</strong> {{ capturedCredentials.password }}</p>
          </div>
          <p class="mt-4 text-center text-sm text-gray-500">Don't have an account? <a href="#" class="text-blue-500">Sign up</a></p>
        </div>
      </div>
  
      <!-- Email Phishing Simulation -->
      <div class="bg-white p-8 rounded shadow-md w-full max-w-2xl mx-auto">
        <h2 class="text-2xl font-bold mb-4">Email Phishing Simulation</h2>
        <p class="mb-4">
          This section simulates an email phishing attack. Below is a fake email that attempts to trick you into entering your credentials.
        </p>
        <div class="border p-4 rounded mb-4">
          <p><strong>From:</strong> support@fakebank.com</p>
          <p><strong>Subject:</strong> Urgent: Verify Your Account</p>
          <p class="mt-4">Dear Customer,</p>
          <p class="mt-2">
            We have detected unusual activity on your account. Please verify your account information by clicking the link below and entering your credentials.
          </p>
          <p class="mt-2">
            <a href="#" @click.prevent="showEmailForm" class="text-blue-500 underline">Verify Your Account</a>
          </p>
          <p class="mt-4">Thank you,</p>
          <p>Fake Bank Support Team</p>
        </div>
        <div v-if="showForm" class="bg-gray-100 p-4 rounded">
          <form @submit.prevent="handleEmailSubmit">
            <div class="mb-4">
              <label for="emailUsername" class="block text-sm font-medium text-gray-700">Username</label>
              <input v-model="emailUsername" type="text" id="emailUsername" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your username" />
            </div>
            <div class="mb-4">
              <label for="emailPassword" class="block text-sm font-medium text-gray-700">Password</label>
              <input v-model="emailPassword" type="password" id="emailPassword" class="mt-1 block w-full border p-2 rounded" placeholder="Enter your password" />
            </div>
            <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full">Submit</button>
          </form>
          <div v-if="capturedEmailCredentials" class="mt-4 p-4 border rounded bg-gray-100">
            <h2 class="text-xl font-bold mb-2">Captured Credentials</h2>
            <p><strong>Username:</strong> {{ capturedEmailCredentials.username }}</p>
            <p><strong>Password:</strong> {{ capturedEmailCredentials.password }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        capturedCredentials: null,
        showForm: false,
        emailUsername: '',
        emailPassword: '',
        capturedEmailCredentials: null
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
      },
      showEmailForm() {
        this.showForm = true;
      },
      handleEmailSubmit() {
        // Simulate capturing the email credentials
        this.capturedEmailCredentials = {
          username: this.emailUsername,
          password: this.emailPassword
        };
  
        // Clear the form
        this.emailUsername = '';
        this.emailPassword = '';
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>