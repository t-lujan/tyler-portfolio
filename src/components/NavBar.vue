<template>
    <header class="navbar">
      <div class="brand">Tyler Lujan</div>
      <div class="subtitle">Junior Front-End Developer</div>
      <button class="hamburger" @click="isOpen = !isOpen">☰</button>
      <nav :class="{ open: isOpen }">
        <RouterLink to="/" @click="isOpen = false">Home</RouterLink>
        <RouterLink to="/projects" @click="isOpen = false">Projects</RouterLink>
        <RouterLink to="/contact" @click="isOpen = false">Contact</RouterLink>
      </nav>
    </header>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  const isOpen = ref(false)
  </script>
  
  <style scoped>
  .navbar {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;
  }
  
  .brand {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .subtitle {
    font-size: 0.9rem;
    color: gray;
  }
  
  .hamburger {
    display: none;
    font-size: 1.5rem;
    background: none;
    border: none;
  }
  
  nav {
    display: flex;
    gap: 1rem;
  }
  
  @media (max-width: 768px) {
    .hamburger {
      display: block;
    }
  
    nav {
      flex-direction: column;
      width: 100%;
      display: none;
    }
  
    nav.open {
      display: flex;
    }
  }
  </style>
  