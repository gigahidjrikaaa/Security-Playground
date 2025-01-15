<template>
    <div class="p-8">
        <h1 class="text-3xl font-bold mb-4">XSS Playground</h1>
        <p class="mb-4">
            Cross-Site Scripting (XSS) is a type of security vulnerability typically found in web applications. XSS allows attackers to inject malicious scripts into content from otherwise trusted websites. This playground demonstrates how XSS can be exploited.
        </p>
        <p class="mb-4">
            Enter a message below and click "Submit" to see how the message is displayed.
        </p>
        <p class="mb-4 italic">
            Hint: Try entering <code>&lt;script&gt;alert('XSS')&lt;/script&gt;</code> as the message.
        </p>
        <hr class="my-4">
        <form @submit.prevent="handleSubmit">
            <div class="mb-4">
            <label for="message" class="block text-sm font-medium text-gray-700">Message</label>
            <input v-model="message" type="text" id="message" class="mt-1 block w-full border p-2" placeholder="Enter your message" />
            </div>
            <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Submit</button>
        </form>
        <div v-if="submittedMessage" class="mt-4 p-4 border rounded bg-gray-100">
            <h2 class="text-xl font-bold mb-2">Submitted Message</h2>
            <div v-html="submittedMessage"></div>
            <!-- Raw Message -->
            <h2 class="text-xl font-bold mb-2">Raw Message</h2>
            <pre class="mt-2">{{ submittedMessage }}</pre>
        </div>
    </div>
</template>
  
  <script>
  export default {
    data() {
      return {
        message: '',
        submittedMessage: null
      };
    },
    methods: {
      handleSubmit() {
        // Simulate storing and displaying the message, potentially allowing XSS
        this.submittedMessage = this.message;
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>