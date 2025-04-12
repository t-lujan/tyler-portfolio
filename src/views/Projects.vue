<template>
  <div class="projects-page">
    <h1>Projects</h1>
    <div class="grid">
      <div class="card" v-for="i in 4" :key="i">
        <img :src="'https://via.placeholder.com/300x200?text=Project+' + i" alt="project"/>
        <h2>Project {{ i }}</h2>
        <p>This is a placeholder description for Project {{ i }}.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.projects-page {
  padding: 2rem;
}
.grid {
  display: grid;
  gap: 1rem;
  grid-template-columns: 1fr;
}
.card {
  border: 1px solid #ddd;
  padding: 1rem;
}
img {
  width: 100%;
  height: auto;
}
@media(min-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
