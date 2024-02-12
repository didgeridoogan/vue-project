<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Chatfish logo" class="logo"
      src="https://raw.githubusercontent.com/didgeridoogan/Dilara-Dogan-Webbsida-Projekt21/master/logga.png" width="125"
      height="125" />

    <div class="wrapper">
      <HelloWorld msg="Chatfish" />

      <nav>
        <!-- <RouterLink to="/">Home</RouterLink> -->
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/profile">Your Profile</RouterLink>
        <RouterLink to="/users">Users</RouterLink>
      </nav>
    </div>
  </header>
  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

</style>
