<template>
    <div class="p-8">
      <h1 class="text-3xl font-bold mb-4">Overview of Cybersecurity and Network Engineering Certifications</h1>
      <p class="mb-4">
        In the rapidly evolving fields of cybersecurity and network engineering, certifications play a crucial role in validating the skills and knowledge of professionals. Below is an overview of some of the most recognized certifications in these domains.
      </p>
      
      <h2 class="text-2xl font-bold mb-2">Cybersecurity Certifications</h2>
      <ul class="list-disc list-inside mb-4">
        <li>
          <strong>Certified Ethical Hacker (CEH):</strong> Offered by EC-Council, this certification focuses on ethical hacking and penetration testing techniques.
          <NuxtLink to="/certifications/ceh" class="text-blue-500 underline">Learn more</NuxtLink>
        </li>
        <li>
          <strong>Offensive Security Certified Professional (OSCP):</strong> Offered by Offensive Security, this certification is known for its rigorous hands-on exam that tests practical penetration testing skills.
          <NuxtLink to="/certifications/oscp" class="text-blue-500 underline">Learn more</NuxtLink>
        </li>
        <li>
          <strong>Certified Information Systems Security Professional (CISSP):</strong> Offered by (ISC)², this certification covers a broad range of cybersecurity topics and is ideal for experienced security practitioners.
        </li>
        <li>
          <strong>CompTIA Security+:</strong> This entry-level certification covers foundational cybersecurity skills and is a good starting point for those new to the field.
        </li>
      </ul>
      
      <h2 class="text-2xl font-bold mb-2">Network Engineering Certifications</h2>
      <ul class="list-disc list-inside mb-4">
        <li>
          <strong>Cisco Certified Network Associate (CCNA):</strong> Offered by Cisco, this certification covers networking fundamentals, IP services, security fundamentals, automation, and programmability.
          <NuxtLink to="/certifications/cisco" class="text-blue-500 underline">Learn more</NuxtLink>
        </li>
        <li>
          <strong>Cisco Certified Network Professional (CCNP):</strong> Also offered by Cisco, this certification validates advanced knowledge and skills in network solutions.
        </li>
        <li>
          <strong>Juniper Networks Certified Internet Associate (JNCIA):</strong> Offered by Juniper Networks, this certification covers networking fundamentals and Junos OS.
        </li>
        <li>
          <strong>CompTIA Network+:</strong> This certification covers essential networking concepts and is vendor-neutral, making it a good choice for those starting in network engineering.
        </li>
      </ul>
      
      <h2 class="text-2xl font-bold mb-2">Additional Resources</h2>
      <ul class="list-disc list-inside mb-4">
        <li><a href="https://www.eccouncil.org/" target="_blank" class="text-blue-500 underline">EC-Council</a></li>
        <li><a href="https://www.offensive-security.com/" target="_blank" class="text-blue-500 underline">Offensive Security</a></li>
        <li><a href="https://www.isc2.org/" target="_blank" class="text-blue-500 underline">(ISC)²</a></li>
        <li><a href="https://www.comptia.org/" target="_blank" class="text-blue-500 underline">CompTIA</a></li>
        <li><a href="https://www.cisco.com/" target="_blank" class="text-blue-500 underline">Cisco</a></li>
        <li><a href="https://www.juniper.net/" target="_blank" class="text-blue-500 underline">Juniper Networks</a></li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Overview'
  };
  </script>
  
  <style scoped>
  /* No additional styles needed as Tailwind CSS is being used */
  </style>