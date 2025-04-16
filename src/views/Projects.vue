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
.projects-page {
  padding: 2rem;
  min-height: 100vh;
  font-family: 'Inter', sans-serif;
  color: inherit;
  box-sizing: border-box;
  overflow-y: auto; /* allow scroll */
}

h1 {
  font-weight: 600;
  font-size: 2rem;
  text-align: center;
  margin-bottom: 2rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.5rem;
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
  transform: scale(1.02);
  border-color: #aaa;
}

.project-card img {
  width: 100%;
  height: auto;
  display: block;
}

.info {
  padding: 1rem;
}

h2 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

p {
  font-size: 0.9rem;
  color: gray;
}

@media (max-width: 768px) {
  .projects-page {
    padding: 1.25rem;
  }

  .project-card img {
    border-radius: 6px;
  }

  h1 {
    font-size: 1.8rem;
  }

  h2 {
    font-size: 1.1rem;
  }
}
</style>
