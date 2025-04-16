<template>
  <div :class="theme" class="app">
    <div class="grid">
      <div class="left">
        <h1>Tyler Lujan</h1>
        <p class="role">Junior Front-End Developer and Technical Support Specialist</p>
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

const isDark = ref(false)
const theme = ref('light')
watch(isDark, () => {
  theme.value = isDark.value ? 'dark' : 'light'
  document.body.className = theme.value
})
</script>

<style scoped>
html, body {
  margin: 0;
  padding: 0;
  overflow: hidden;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}


.app {
  font-family: 'Inter', sans-serif;

  height: 100vh;
  width: 100vw;
  overflow: hidden;
  font-family: 'Helvetica Neue', sans-serif;
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

h1 {
  font-weight: 600;
  letter-spacing: -0.5px;
  font-size: 2rem;
  margin-bottom: 0.2rem;
}

.role {
  font-weight: 300;
  font-size: 0.85rem;
  letter-spacing: 0.3px;
  color: #777;
}

nav ul {
  list-style: none;
  padding: 0;
}

nav li {
  margin: 1rem 0;
}

nav a {
  text-decoration: none;
  font-weight: 500;
  color: inherit;
  transition: color 0.3s ease;
  position: relative;
}

nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -4px;
  height: 1px;
  width: 0;
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
@media (max-width: 768px) {
  .grid {
    display: flex;
    flex-direction: column;
  }

  .left {
    width: 100%;
    padding: 1.5rem 1.5rem 0 1.5rem;
    text-align: center;
  }

  .left nav ul {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    padding: 0;
  }

  .right {
    width: 100%;
    padding: 1.5rem;
    overflow: visible;
  }

  .theme-toggle {
    position: static;
    margin-top: 1rem;
    text-align: center;
  }
}



</style>
