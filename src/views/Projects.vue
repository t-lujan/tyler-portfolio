<template>
  <div class="projects-page">
    <h1>Projects</h1>
    <div class="grid">
      <div class="project" v-for="n in 4" :key="n">
        <img :src="`https://via.placeholder.com/400x240?text=Project+${n}`" />
        <h2>Project {{ n }}</h2>
        <p>Brief description of project {{ n }}.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.projects-page {
  padding: 2rem;
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
}

.grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
}

.project {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 8px;
  background: var(--bg, white);
  text-align: center;
}

.project img {
  width: 100%;
  height: auto;
  border-radius: 4px;
}

@media (max-width: 768px) {
  .projects-page {
    padding: 1rem;
  }

  h1 {
    font-size: 1.5rem;
  }

  .project p {
    font-size: 0.85rem;
  }
}
</style>
