<template>
  <div class="projects-page">
    <h1>Projects</h1>

    <div class="projects-grid">
      <div class="project-card" v-for="n in 4" :key="n">
        <img :src="`https://via.placeholder.com/280x160?text=Project+${n}`" :alt="`Project ${n}`" />
        <div class="info">
          <h2>Project {{ n }}</h2>
          <p>This is a placeholder description for Project {{ n }}.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// no JS needed
</script>

<style scoped>
@media (max-width: 768px) {
  .projects-page {
    padding: 1.5rem;
    overflow-y: auto;
    max-height: 100vh;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .project-card img {
    height: auto;
    max-height: 160px;
    object-fit: cover;
  }
}

.projects-page {
  padding: 3rem 4rem;
  min-height: 100vh;
  font-family: 'Inter', sans-serif;
  color: inherit;
  box-sizing: border-box;
  overflow-y: auto; /* Allow scrolling */
}

h1 {
  font-weight: 600;
  font-size: 2.5rem;
  text-align: center;
  margin-bottom: 3rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2.5rem;
}

.project-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid #ccc;
  border-radius: 12px;
  overflow: hidden;
  transition: all 0.3s ease;
  height: 100%;
}

.project-card:hover {
  transform: scale(1.03);
  border-color: #aaa;
}

.project-card img {
  width: 100%;
  height: auto;
  display: block;
}

.info {
  padding: 1.25rem;
}

h2 {
  font-size: 1.4rem;
  margin-bottom: 0.5rem;
}

p {
  font-size: 0.95rem;
  color: gray;
}

/* MOBILE ONLY */
@media (max-width: 768px) {
  .projects-page {
    padding: 1rem;
    overflow-y: auto;
  }

  h1 {
    font-size: 2rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-card img {
    max-width: 100%;
    height: auto;
  }

  .project-card {
    padding: 0.5rem;
  }

  h2 {
    font-size: 1.2rem;
  }

  p {
    font-size: 0.9rem;
  }
}
</style>
