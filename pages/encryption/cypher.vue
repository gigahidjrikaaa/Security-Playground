<template>
    <div>
      <h1 class="text-3xl font-bold">Cypher</h1>
      <p>Cypher is a method of encrypting text. It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet. For example, with a shift of 1, A would be replaced by B, B would become C, and so on.</p>
      <p>Enter text below to encrypt it using the cypher method.</p>
      <select v-model="selectedCipher" class="border p-2 w-full mb-2">
        <option value="caesar">Caesar Cipher</option>
        <option value="atbash">Atbash Cipher</option>
        <option value="rot13">ROT13</option>
      </select>
      <textarea v-model="inputText" class="border p-2 w-full" placeholder="Enter text to encrypt"></textarea>
      <button @click="encryptText" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2">Encrypt</button>
      <p class="mt-2">Encrypted text: {{ encryptedText }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedCipher: 'caesar',
        shift: 3, // Default shift for Caesar Cipher
        inputText: '',
        encryptedText: ''
      };
    },
    methods: {
      encryptText() {
        if (this.selectedCipher === 'caesar') {
          this.encryptedText = this.caesarCipher(this.inputText, this.shift);
        } else if (this.selectedCipher === 'atbash') {
          this.encryptedText = this.atbashCipher(this.inputText);
        } else if (this.selectedCipher === 'rot13') {
          this.encryptedText = this.rot13Cipher(this.inputText);
        }
      },
      caesarCipher(text, shift) {
        return text.replace(/[a-z]/gi, (char) => {
          const start = char <= 'Z' ? 65 : 97;
          return String.fromCharCode(((char.charCodeAt(0) - start + shift) % 26) + start);
        });
      },
      atbashCipher(text) {
        return text.replace(/[a-z]/gi, (char) => {
          const start = char <= 'Z' ? 65 : 97;
          return String.fromCharCode(start + 25 - (char.charCodeAt(0) - start));
        });
      },
      rot13Cipher(text) {
        return text.replace(/[a-z]/gi, (char) => {
          const start = char <= 'Z' ? 65 : 97;
          return String.fromCharCode(((char.charCodeAt(0) - start + 13) % 26) + start);
        });
      }
    }
  };
  </script>