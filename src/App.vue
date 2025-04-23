<template>
  <div class="app">
    <div :class="['grid', { 'mobile-grid': isMobile && route.name !== 'Home' }]">
      <!-- ───────────── LEFT (sidebar / header) ───────────── -->
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

      <!-- ───────────── RIGHT (page outlet) ───────────── -->
      <div class="right">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted, onBeforeUnmount } from 'vue'
import { useRoute } from 'vue-router'

/* ── routing ── */
const route = useRoute()

/* ── dark / light toggle ── */
const isDark = ref(false)
watch(isDark, () => {
  // preserve any existing body classes
  document.body.classList.toggle('dark', isDark.value)
})

/* ── mobile detection (live) ── */
const isMobile = ref(false)
function checkMobile () {
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

<style scoped>
/* ═══════════════════════════════════════════════════════ */
/*  GLOBAL / RESET  */
/* ═══════════════════════════════════════════════════════ */
*, *::before, *::after {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden;   /* stop rogue horizontal scroll */
}

/* ═══════════════════════════════════════════════════════ */
/*  APP WRAPPER  */
/* ═══════════════════════════════════════════════════════ */
.app {
  font-family: 'Helvetica Neue', sans-serif;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-y: auto;
  transition: background-color 0.3s ease, color 0.3s ease;
  background-color: white;
  color: black;
}

body.dark .app {
  background-color: #121212;
  color: #f1f1f1;
}



/* ═══════════════════════════════════════════════════════ */
/*  GRID LAYOUT  */
/* ═══════════════════════════════════════════════════════ */
.grid {
  display: grid;
  grid-template-columns: 300px 1fr; /* desktop two-col */
  width: 100%;
  max-width: 1280px;
  height: 100%;
  margin: 0 auto;
}

/* LEFT SIDEBAR / HEADER */
.left {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  padding: 2rem;
  position: relative;
}

/* RIGHT CONTENT PANE */
.right {
  position: relative;
  overflow: hidden;
  height: 100%;
}

/* ─── typography ─── */
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

/* ─── nav ─── */
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

/* ─── theme toggle ─── */
.theme-toggle {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  font-size: 0.8rem;
}

/* ═══════════════════════════════════════════════════════ */
/*  MOBILE BREAKPOINT  */
/* ═══════════════════════════════════════════════════════ */
@media (max-width: 768px) {
  /* collapse grid so no phantom 300 px col remains */
  .grid {
    grid-template-columns: 1fr;
  }

  .mobile-grid {
    display: flex;
    flex-direction: column;
    width: 100%;
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
    width: 100%;
    padding: 1rem;
    overflow: visible; /* allow page scrolling */
  }

  .mobile-grid {
    min-height: 100vh; /* full height to anchor toggle at bottom */
    position: relative;
    padding-bottom: 4rem; /* space for toggle */
  }
  
  .mobile-grid .theme-toggle {
    position: absolute;
    bottom: 1.5rem;
    left: 0;
    right: 0;
    text-align: center;
    font-size: 0.8rem;
  }
  
}
</style>
