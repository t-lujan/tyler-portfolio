<template>
  <div class="page-container">
    <div class="content">
      <h1>Projects</h1>
      <div class="projects-grid">
        <div v-for="n in 4" :key="n" class="project-card">
          <img :src="`https://via.placeholder.com/300x180?text=Project+${n}`" alt="Project" />
          <h2>Project {{ n }}</h2>
          <p>This is a placeholder description for Project {{ n }}.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.page-container {
  padding: 2rem;
  width: 100%;
  box-sizing: border-box;
}

h1 {
  font-size: 2rem;
  text-align: center;
  margin-bottom: 1.5rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.5rem;
}

.project-card {
  border: 1px solid #ddd;
  padding: 1rem;
  border-radius: 8px;
  background-color: white;
  text-align: center;
}

.project-card img {
  width: 100%;
  height: auto;
  border-radius: 4px;
}

@media (max-width: 768px) {
  h1 {
    font-size: 1.6rem;
  }

  .page-container {
    padding: 1rem;
  }

  .project-card p {
    font-size: 0.85rem;
  }
}
</style>
