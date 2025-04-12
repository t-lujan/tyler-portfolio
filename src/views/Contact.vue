<template>
  <div class="contact-page">
    <h1>Contact Me</h1>
    <form @submit.prevent>
      <input type="text" placeholder="Name" />
      <input type="email" placeholder="Email" />
      <textarea placeholder="Message"></textarea>
      <button type="submit">Send</button>
    </form>
  </div>
</template>

<style scoped>
.contact-page {
  padding: 2rem;
}
form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
input, textarea {
  padding: 0.75rem;
  font-size: 1rem;
  border: 1px solid #ccc;
}
button {
  padding: 0.75rem;
  background: black;
  color: white;
  border: none;
}
</style>
