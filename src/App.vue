<template>
  <div :class="theme" class="app">
    <div :class="['grid', { 'mobile-grid': isMobile && route.name !== 'Home' }]">
      <div class="left">
        <h1>Tyler Lujan</h1>
        <p class="role">
          <span>Junior Front-End Developer</span><br />
          <span>Technical Support Specialist</span>
        </p>
        
        <nav>
          <ul>
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/projects">Projects</router-link></li>
            <li><router-link to="/contact">Contact</router-link></li>
          </ul>
        </nav>
        <div class="theme-toggle">
          <label>
            <input type="checkbox" v-model="isDark" />
            {{ isDark ? 'DARK' : 'LIGHT' }}
          </label>
        </div>
      </div>

      <div class="right">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const isDark = ref(false)
const theme = ref('light')
watch(isDark, () => {
  theme.value = isDark.value ? 'dark' : 'light'
  document.body.className = theme.value
})

const isMobile = /Mobi|Android|iPhone|iPad/i.test(navigator.userAgent)
</script>

<style scoped>

html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden; /* 🔧 prevent horizontal scroll */
  box-sizing: border-box;
}

.app {
  font-family: 'Helvetica Neue', sans-serif;
  height: 100vh;
  width: 100vw;
  overflow-x: hidden;
  overflow-y: auto;
  display: flex;
}

.dark {
  background-color: #111;
  color: white;
}

.grid {
  display: grid;
  grid-template-columns: 300px 1fr;
  width: 100%;
  height: 100%;
}

.left {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  padding: 2rem;
  position: relative;
}

.right {
  position: relative;
  overflow: hidden;
  height: 100%;
}

/* ✂ header styles */
h1 {
  font-weight: 600;
  font-size: 2rem;
  margin-bottom: 0.2rem;
  letter-spacing: -0.5px;
}

.role {
  font-weight: 300;
  font-size: 0.85rem;
  color: #777;
  letter-spacing: 0.3px;
}

/* ✂ nav styles */
nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

nav li {
  margin: 1rem 0;
}

nav a {
  text-decoration: none;
  font-weight: 500;
  color: inherit;
  position: relative;
  transition: color 0.3s ease;
}

nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 0;
  height: 1px;
  background-color: currentColor;
  transition: width 0.3s ease;
}

nav a:hover::after {
  width: 100%;
}

.theme-toggle {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  font-size: 0.8rem;
}


/* ✅ MOBILE FIXES */
@media (max-width: 768px) {

  .role {
    font-size: 0.85rem;
    line-height: 1.4;
  }
  .mobile-grid {
    display: flex;
    flex-direction: column;
    width: 100%;
    overflow-x: hidden;
  }

  .mobile-grid .left {
    width: 100%;
    padding: 1.5rem;
    text-align: center;
  }

  .mobile-grid .left nav ul {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    padding: 0;
    flex-wrap: wrap;
  }

  .mobile-grid .right {
    width: 100%;
    padding: 1rem;
    overflow: visible;
  }

  .mobile-grid .theme-toggle {
    position: static;
    margin-top: 1rem;
    text-align: center;
  }
}
</style>