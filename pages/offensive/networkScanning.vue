<template>
    <div class="p-8">
      <h1 class="text-3xl font-bold mb-4">Network Scanning Playground</h1>
      <p class="mb-4">
        Network scanning is a process used to discover active devices on a network and gather information about them. This simulation demonstrates how a network scanner like Nmap works.
      </p>
      <p class="mb-4">
        Enter an IP address or range below and click "Scan" to simulate a network scan.
      </p>
      <div class="mb-4">
        <label for="target" class="block text-sm font-medium text-gray-700">Target IP Address or Range</label>
        <input v-model="target" type="text" id="target" class="mt-1 block w-full border p-2 rounded" placeholder="e.g., 192.168.1.1 or 192.168.1.0/24" />
      </div>
      <button @click="simulateScan" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Scan</button>
      <div v-if="isScanning" class="mt-4">
        <p>Scanning...</p>
        <div class="w-full bg-gray-200 rounded-full h-4">
          <div :style="{ width: progress + '%' }" class="bg-blue-500 h-4 rounded-full transition-all duration-1000"></div>
        </div>
      </div>
      <div v-if="scanResults" class="mt-4 p-4 border rounded bg-gray-100">
        <h2 class="text-xl font-bold mb-2">Scan Results</h2>
        <pre class="bg-black text-green-500 p-4 rounded h-64 overflow-y-scroll">{{ scanResults }}</pre>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        target: '',
        isScanning: false,
        progress: 0,
        scanResults: null
      };
    },
    methods: {
      simulateScan() {
        this.isScanning = true;
        this.progress = 0;
        this.scanResults = null;
  
        const interval = setInterval(() => {
          if (this.progress < 100) {
            this.progress += 10;
          } else {
            clearInterval(interval);
            this.isScanning = false;
            this.scanResults = this.generateScanResults(this.target);
          }
        }, 500);
      },
      generateScanResults(target) {
        // Simulate scan results
        return `
  Starting Nmap 7.80 ( https://nmap.org ) at 2023-10-10 12:00 UTC
  Nmap scan report for ${target}
  Host is up (0.00013s latency).
  Not shown: 997 closed ports
  PORT    STATE SERVICE
  22/tcp  open  ssh
  80/tcp  open  http
  443/tcp open  https
  
  Nmap done: 1 IP address (1 host up) scanned in 0.58 seconds
        `;
      }
    }
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>