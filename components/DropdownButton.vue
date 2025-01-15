<template>
    <div>
      <button @click="toggleDropdown" class="block w-full text-left p-4 hover:bg-gray-600" :class="{'bg-gray-900': isDropdownOpen}">
        {{ title }}
      </button>
      <ul v-if="isDropdownOpen" class="pl-4">
        <slot></slot>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        isDropdownOpen: false
      };
    },
    methods: {
      toggleDropdown() {
        this.isDropdownOpen = !this.isDropdownOpen;
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>