<template>
    <div>
      <h1 class="text-3xl font-bold mb-4">Password Checker</h1>
      <input v-model="password" type="password" class="border p-2 w-full mb-2" placeholder="Enter your password" />
      <p class="mt-2">Password strength: <span :class="strengthClass">{{ passwordStrength }}</span></p>
      <ul class="mt-2">
        <li :class="{'text-green-500': hasLength, 'text-red-500': !hasLength}">At least 8 characters</li>
        <li :class="{'text-green-500': hasUppercase, 'text-red-500': !hasUppercase}">At least one uppercase letter</li>
        <li :class="{'text-green-500': hasLowercase, 'text-red-500': !hasLowercase}">At least one lowercase letter</li>
        <li :class="{'text-green-500': hasNumber, 'text-red-500': !hasNumber}">At least one number</li>
        <li :class="{'text-green-500': hasSpecialChar, 'text-red-500': !hasSpecialChar}">At least one special character</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        password: ''
      };
    },
    computed: {
      hasLength() {
        return this.password.length >= 8;
      },
      hasUppercase() {
        return /[A-Z]/.test(this.password);
      },
      hasLowercase() {
        return /[a-z]/.test(this.password);
      },
      hasNumber() {
        return /[0-9]/.test(this.password);
      },
      hasSpecialChar() {
        return /[!@#$%^&*(),.?":{}|<>]/.test(this.password);
      },
      passwordStrength() {
        const criteria = [this.hasLength, this.hasUppercase, this.hasLowercase, this.hasNumber, this.hasSpecialChar];
        const metCriteria = criteria.filter(criterion => criterion).length;
  
        if (metCriteria === 5) {
          return 'Very Strong';
        } else if (metCriteria >= 4) {
          return 'Strong';
        } else if (metCriteria >= 3) {
          return 'Medium';
        } else {
          return 'Weak';
        }
      },
      strengthClass() {
        switch (this.passwordStrength) {
          case 'Very Strong':
            return 'text-green-500';
          case 'Strong':
            return 'text-blue-500';
          case 'Medium':
            return 'text-yellow-500';
          case 'Weak':
            return 'text-red-500';
          default:
            return '';
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>