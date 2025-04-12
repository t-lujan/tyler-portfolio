<template>
    <header class="navbar">
      <div class="logo">Tyler Lujan</div>
      <button class="hamburger" @click="showMenu = !showMenu">
        ☰
      </button>
      <nav :class="{ open: showMenu }">
        <RouterLink to="/" @click="showMenu = false">Home</RouterLink>
        <RouterLink to="/projects" @click="showMenu = false">Projects</RouterLink>
        <RouterLink to="/contact" @click="showMenu = false">Contact</RouterLink>
        <label class="theme-toggle">
          <input type="checkbox" v-model="isDark" @change="$emit('toggleDark')" />
          <span>{{ isDark ? 'DARK' : 'LIGHT' }}</span>
        </label>
      </nav>
    </header>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  const props = defineProps(['isDark'])
  const showMenu = ref(false)
  </script>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
  }
  .logo {
    font-weight: bold;
    font-size: 1.4rem;
  }
  nav {
    display: none;
  }
  nav.open {
    display: flex;
    flex-direction: column;
  }
  .hamburger {
    font-size: 1.6rem;
    background: none;
    border: none;
  }
  .theme-toggle {
    margin-top: 1rem;
    font-size: 0.8rem;
  }
  @media(min-width: 768px) {
    .hamburger {
      display: none;
    }
    nav {
      display: flex !important;
      gap: 1rem;
      flex-direction: row;
    }
  }
  </style>
  