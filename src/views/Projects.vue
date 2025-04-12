<template>
  <div class="page">
    <header class="mobile-header" v-if="isMobile">
      <div class="header-content">
        <h1>Tyler Lujan</h1>
        <p>Junior Front-End Developer and Technical Support Specialist</p>
      </div>
      <button class="burger" @click="toggleMenu">☰</button>
      <nav v-if="showMenu" class="mobile-nav">
        <router-link @click="closeMenu" to="/">Home</router-link>
        <router-link @click="closeMenu" to="/projects">Projects</router-link>
        <router-link @click="closeMenu" to="/contact">Contact</router-link>
      </nav>
    </header>

    <div class="content">
      <h2 class="page-title">Projects</h2>
      <div class="project-grid">
        <div class="project-card" v-for="n in 4" :key="n">
          <img :src="`https://via.placeholder.com/300x200?text=Project+${n}`" :alt="`Project ${n}`" />
          <h3>Project {{ n }}</h3>
          <p>This is a placeholder description for Project {{ n }}.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isMobile = ref(false)
const showMenu = ref(false)

const toggleMenu = () => {
  showMenu.value = !showMenu.value
}

const closeMenu = () => {
  showMenu.value = false
}

onMounted(() => {
  isMobile.value = window.innerWidth < 768
})
</script>

<style scoped>
.page {
  padding: 2rem;
}

.page-title {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.project-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 1rem;
  text-align: center;
  background: white;
}

.project-card img {
  width: 100%;
  border-radius: 4px;
  margin-bottom: 0.5rem;
}

/* Mobile header */
.mobile-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  text-align: center;
  margin-bottom: 2rem;
}

.header-content {
  flex: 1 1 100%;
  margin-bottom: 1rem;
}

.burger {
  background: none;
  border: none;
  font-size: 2rem;
  cursor: pointer;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  font-size: 1.2rem;
}

.mobile-nav a {
  text-decoration: none;
}
</style>
