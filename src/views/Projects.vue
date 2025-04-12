<template>
  <div class="projects-container">
    <h1>Projects</h1>
    <div class="project-list">
      <div class="project-card" v-for="n in 4" :key="n">
        <img :src="`https://via.placeholder.com/400x240?text=Project+${n}`" alt="Project image" />
        <h2>Project {{ n }}</h2>
        <p>This is a placeholder description for project {{ n }}.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.projects-container {
  padding: 2rem;
  max-width: 960px;
  margin: auto;
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
}

.project-list {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  justify-content: center;
}

.project-card {
  width: 100%;
  max-width: 360px;
  background: white;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: center;
}

.project-card img {
  width: 100%;
  height: auto;
  border-radius: 4px;
  margin-bottom: 1rem;
}

@media (max-width: 768px) {
  .projects-container {
    padding: 1rem;
  }

  h1 {
    font-size: 1.5rem;
  }

  .project-card p {
    font-size: 0.9rem;
  }
}
</style>
