<template>
    <div class="p-8">
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
  
      <h1 class="text-2xl font-bold mt-4">Brute Force Simulation</h1>
      <p class="mb-4">This simulation demonstrates how long it would take to crack a password using a brute force attack.</p>
      <p class="mb-4">Enter the password length and click "Simulate" to see the time required to crack the password.</p>
      <div class="mb-4">
        <label for="length" class="block text-sm font-medium text-gray-700">Password Length</label>
        <input v-model.number="length" type="number" id="length" class="mt-1 block w-full border p-2" placeholder="Enter password length" />
      </div>
      <button @click="simulateBruteForce" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Simulate</button>
      <div v-if="isSimulating" class="mt-4">
        <p>Simulating brute force attack...</p>
        <div class="w-full bg-gray-200 rounded-full h-4">
          <div :style="{ width: progress + '%' }" class="bg-blue-500 h-4 rounded-full transition-all duration-1000"></div>
        </div>
        <div class="mt-4 bg-black text-green-500 p-4 rounded h-64 overflow-y-scroll">
          <p v-for="(guess, index) in bruteForceGuesses" :key="index">{{ guess }}</p>
        </div>
      </div>
      <p v-if="bruteForceTime" class="mt-4">Estimated time to crack the password: {{ bruteForceTime }}</p>
  
      <h1 class="text-2xl font-bold mt-4">Dictionary Attack Simulation</h1>
      <p class="mb-4">This simulation demonstrates how long it would take to crack a password using a dictionary attack.</p>
      <button @click="simulateDictionaryAttack" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Simulate Dictionary Attack</button>
      <div v-if="isDictionarySimulating" class="mt-4">
        <p>Simulating dictionary attack...</p>
        <div class="w-full bg-gray-200 rounded-full h-4">
          <div :style="{ width: dictionaryProgress + '%' }" class="bg-blue-500 h-4 rounded-full transition-all duration-1000"></div>
        </div>
        <div class="mt-4 bg-black text-green-500 p-4 rounded h-64 overflow-y-scroll">
          <p v-for="(guess, index) in dictionaryGuesses" :key="index">{{ guess }}</p>
        </div>
      </div>
      <p v-if="dictionaryAttackTime" class="mt-4">Estimated time to crack the password: {{ dictionaryAttackTime }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        password: '',
        length: 8,
        bruteForceTime: null,
        isSimulating: false,
        progress: 0,
        bruteForceGuesses: [],
        isDictionarySimulating: false,
        dictionaryProgress: 0,
        dictionaryGuesses: [],
        dictionaryAttackTime: null,
        commonPasswords: [
          '123456', 'password', '123456789', '12345678', '12345', '1234567', '1234567890', 'qwerty', 'abc123', 'password1'
        ]
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
    },
    methods: {
      simulateBruteForce() {
        this.isSimulating = true;
        this.progress = 0;
        this.bruteForceTime = null;
        this.bruteForceGuesses = [];
  
        const charset = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*(),.?":{}|<>';
        const charsetSize = charset.length;
        const combinations = Math.pow(charsetSize, this.length);
        const attemptsPerSecond = 1000000000; // 1 billion attempts per second
        const seconds = combinations / attemptsPerSecond;
  
        const years = Math.floor(seconds / (365 * 24 * 60 * 60));
        const days = Math.floor((seconds % (365 * 24 * 60 * 60)) / (24 * 60 * 60));
        const hours = Math.floor((seconds % (24 * 60 * 60)) / (60 * 60));
        const minutes = Math.floor((seconds % (60 * 60)) / 60);
        const secs = Math.floor(seconds % 60);
  
        this.bruteForceTime = `${years} years, ${days} days, ${hours} hours, ${minutes} minutes, ${secs} seconds`;
  
        let guess = '';
        let index = 0;
  
        const interval = setInterval(() => {
          if (index < this.password.length) {
            const charIndex = Math.floor(Math.random() * charsetSize);
            guess += charset[charIndex];
            this.bruteForceGuesses.push(guess);
            index++;
          } else {
            clearInterval(interval);
            this.isSimulating = true;
          }
        }, 100);
  
        const progressInterval = setInterval(() => {
          if (this.progress < 100) {
            this.progress += 10;
          } else {
            clearInterval(progressInterval);
          }
        }, 1000);
      },
      simulateDictionaryAttack() {
        this.isDictionarySimulating = true;
        this.dictionaryProgress = 0;
        this.dictionaryGuesses = [];
        this.dictionaryAttackTime = null;
  
        const attemptsPerSecond = 1000; // 1 thousand attempts per second
        const totalPasswords = this.commonPasswords.length;
        const seconds = totalPasswords / attemptsPerSecond;
  
        const interval = setInterval(() => {
          if (this.dictionaryProgress < 100) {
            this.dictionaryProgress += (100 / totalPasswords);
            const index = Math.floor(this.dictionaryProgress / (100 / totalPasswords));
            const guess = this.commonPasswords[index];
            this.dictionaryGuesses.push(guess);
            if (guess === this.password) {
              clearInterval(interval);
              this.isDictionarySimulating = true;
              this.dictionaryAttackTime = `Password cracked in ${index + 1} attempts`;
            }
          } else {
            clearInterval(interval);
            this.isDictionarySimulating = true;
            this.dictionaryAttackTime = 'Password not found in common passwords list';
          }
        }, 1000 / attemptsPerSecond);
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>