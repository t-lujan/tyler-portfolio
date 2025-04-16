<template>
    <nav :class="['nav-bar', { 'mobile-nav': isMobile }]">
      <div class="header">
        <h1>Tyler Lujan</h1>
        <p>Junior Front-End Developer and Technical Support Specialist</p>
      </div>
      <div class="menu" v-if="isMobile">
        <button @click="toggleMenu" class="hamburger">☰</button>
        <div v-show="menuOpen" class="dropdown">
          <router-link @click="closeMenu" to="/">Home</router-link>
          <router-link @click="closeMenu" to="/projects">Projects</router-link>
          <router-link @click="closeMenu" to="/contact">Contact</router-link>
        </div>
      </div>
      <div v-else class="links">
        <router-link to="/">Home</router-link>
        <router-link to="/projects">Projects</router-link>
        <router-link to="/contact">Contact</router-link>
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    data() {
      return {
        menuOpen: false,
        isMobile: false,
      }
    },
    mounted() {
      this.isMobile = window.innerWidth <= 768
    },
    methods: {
      toggleMenu() {
        this.menuOpen = !this.menuOpen
      },
      closeMenu() {
        this.menuOpen = false
      }
    }
  }
  </script>
  
  <style scoped>
  .nav-bar {
    display: flex;
    justify-content: space-between;
    padding: 1rem;
    font-family: sans-serif;
  }
  
  .header h1 {
    font-size: 1.5rem;
    margin: 0;
  }
  .header p {
    font-size: 0.875rem;
    color: #555;
    margin: 0;
  }
  
  .links a,
  .dropdown a {
    margin: 0 0.5rem;
    text-decoration: none;
  }
  
  .hamburger {
    font-size: 2rem;
    background: none;
    border: none;
    cursor: pointer;
  }
  
  .dropdown {
    display: flex;
    flex-direction: column;
    margin-top: 0.5rem;
  }
  
  @media screen and (max-width: 768px) {
    .nav-bar {
      flex-direction: column;
      align-items: flex-start;
    }
  }
  </style>
  