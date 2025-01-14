<script setup lang="ts">
const version = 2 + 1
</script>

<template>
  <div class="dashboard">
    <aside class="sidebar">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Profile</a></li>
        <li><a href="#">Settings</a></li>
        <li><a href="#">Logout</a></li>
      </ul>
    </aside>
    <main class="content">
      <div class="hello">
        Hello Nuxt {{ version }}!
      </div>
    </main>
  </div>
</template>

<style scoped>
.dashboard {
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 250px;
  background-color: #2c3e50;
  color: white;
  padding: 1rem;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar ul li {
  margin: 1rem 0;
}

.sidebar ul li a {
  color: white;
  text-decoration: none;
}

.content {
  flex: 1;
  padding: 2rem;
}

.hello {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 3rem;
}
</style>