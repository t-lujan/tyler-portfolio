<template>
  <div class="home">
    <!-- Sidebar Navigation -->
    <nav :class="['sidebar', { 'sidebar--collapsed': isSidebarCollapsed }]">
      <button class="sidebar__toggle" @click="toggleSidebar">
        ☰
      </button>
      <ul class="sidebar__menu">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/projects">Projects</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
    </nav>

    <!-- Main Content -->
    <div class="content">
      <canvas ref="pongCanvas" class="pong-bg"></canvas>
      <div class="about">
        <p>
          I’m a junior dev focused on crafting clean, efficient, and interactive web experiences.
          My passion is building thoughtful UI/UX with Vue.js, JavaScript, and modern front-end tools.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const pongCanvas = ref(null);
    const isSidebarCollapsed = ref(true);

    const toggleSidebar = () => {
      isSidebarCollapsed.value = !isSidebarCollapsed.value;
    };

    onMounted(() => {
      // Pong game initialization code here
    });

    return {
      pongCanvas,
      isSidebarCollapsed,
      toggleSidebar,
    };
  },
};
</script>

<style scoped>
/* Base Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Layout */
.home {
  display: flex;
  flex-direction: row;
  height: 100vh;
}

/* Sidebar Navigation */
.sidebar {
  width: 250px;
  background-color: #f1f1f1;
  transition: transform 0.3s ease;
}

.sidebar--collapsed {
  transform: translateX(-100%);
}

.sidebar__toggle {
  display: none;
  background: none;
  border: none;
  font-size: 2rem;
  cursor: pointer;
}

.sidebar__menu {
  list-style-type: none;
  padding: 1rem;
}

.sidebar__menu li {
  margin: 1rem 0;
}

.sidebar__menu a {
  text-decoration: none;
  color: #333;
}

/* Main Content */
.content {
  flex-grow: 1;
  position: relative;
}

.pong-bg {
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, #ccc 0%, transparent 100%);
}

.about {
  position: absolute;
  bottom: 3rem;
  right: 3rem;
  max-width: 300px;
  font-size: 0.9rem;
  text-align: right;
  line-height: 1.5;
}

/* Responsive Design */
@media (max-width: 768px) {
  .sidebar {
    position: absolute;
    z-index: 10;
    height: 100%;
  }

  .sidebar__toggle {
    display: block;
    position: absolute;
    top: 1rem;
    left: 1rem;
  }

  .content {
    margin-left: 0;
  }
}
</style>
