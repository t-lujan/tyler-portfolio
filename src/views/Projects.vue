<template>
  <div class="projects-page">
    <h1>Projects</h1>
    <div class="project-grid">
      <div class="project" v-for="n in 4" :key="n">
        <img :src="`https://via.placeholder.com/300x200?text=Project+${n}`" :alt="`Project ${n}`" />
        <h3>Project {{ n }}</h3>
        <p>This is a placeholder description for Project {{ n }}.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.projects-page {
  padding: 2rem;
  overflow-y: auto;
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1.5rem;
}

.project {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 8px;
  background: var(--color-bg);
  text-align: center;
}

.project img {
  width: 100%;
  height: auto;
  border-radius: 4px;
}
</style>
