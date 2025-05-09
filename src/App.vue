<template>
  <div :class="['app', isDark ? 'dark' : 'light']">
    <div :class="['grid', { 'mobile-grid': isMobile && route.name !== 'Home' }]">
      <!-- LEFT SIDE -->
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

        <!-- THEME TOGGLE -->
        <div
          :class="[
            'theme-toggle',
            {
              'bottom-left': isMobile && isHomePage,
              'bottom-flow': isMobile && !isHomePage,
              'desktop-fixed': !isMobile
            }
          ]"
        >
          <label>
            <input type="checkbox" v-model="isDark" />
            {{ isDark ? 'DARK' : 'LIGHT' }}
          </label>
        </div>
      </div>

      <!-- RIGHT PANE -->
      <div class="right">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted, onBeforeUnmount, computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isDark = ref(false)
const isHomePage = computed(() => route.name === 'Home')

// Mobile detection
const isMobile = ref(false)
function checkMobile() {
  isMobile.value =
    /Mobi|Android|iPhone|iPad/i.test(navigator.userAgent) ||
    window.innerWidth <= 768
}
onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})
onBeforeUnmount(() => window.removeEventListener('resize', checkMobile))
</script>

<style>
/* RESET */
*, *::before, *::after {
  box-sizing: border-box;
}
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden;
}

/* APP WRAPPER */
.app {
  font-family: 'Helvetica Neue', sans-serif;
  min-height: 100vh;
  width: 100%;
  overflow-y: auto;
}

/* LAYOUT GRID */
.grid {
  display: grid;
  grid-template-columns: 300px 1fr;
  width: 100%;
  max-width: 1280px;
  height: 100%;
  margin: 0 auto;
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
  padding: 2rem;
}

/* TYPOGRAPHY */
h1 {
  font-weight: 600;
  font-size: 2rem;
  margin-bottom: 0.2rem;
}
.role {
  font-weight: 300;
  font-size: 0.85rem;
  color: inherit;
}

/* NAV */
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

/* TOGGLE POSITIONS */
.theme-toggle.desktop-fixed {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  font-size: 0.8rem;
}
@media (max-width: 768px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .mobile-grid {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding-bottom: 4rem;
    position: relative;
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
    flex-wrap: wrap;
  }

  .mobile-grid .right {
    padding: 1rem;
  }

  .theme-toggle.bottom-left {
    position: fixed;
    bottom: 1rem;
    left: 1rem;
    font-size: 0.8rem;
    z-index: 10;
  }

  .theme-toggle.bottom-flow {
    margin-top: 2rem;
    text-align: center;
    font-size: 0.8rem;
  }
}

/* THEME COLORS */
.light {
  background-color: #fff;
  color: #111;
}

.dark {
  background-color: #111;
  color: #eee;
}

.dark a {
  color: #eee;
}

.dark input,
.dark textarea {
  background-color: #222;
  color: #eee;
  border: 1px solid #444;
}

.dark .card {
  background-color: #1a1a1a;
  color: #eee;
}
</style>
