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
      <h2 class="page-title">Contact Me</h2>
      <form @submit.prevent class="form">
        <input type="text" placeholder="Name" required />
        <input type="email" placeholder="Email" required />
        <textarea placeholder="Message" required></textarea>
        <button type="submit">Send</button>
      </form>
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

.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 500px;
  margin: 0 auto;
}

input,
textarea {
  padding: 0.75rem;
  font-size: 1rem;
  border-radius: 5px;
  border: 1px solid #ccc;
}

button {
  background: black;
  color: white;
  padding: 0.75rem;
  border: none;
  border-radius: 5px;
  font-weight: bold;
  cursor: pointer;
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
