<template>
  <div class="contact-page">
    <h1>Contact Me</h1>
    <form class="contact-form" action="mailto:tyler@example.com" method="POST" enctype="text/plain">
      <input type="text" name="name" placeholder="Name" required />
      <input type="email" name="email" placeholder="Email" required />
      <textarea name="message" placeholder="Message" required></textarea>
      <button type="submit">Send</button>
    </form>
  </div>
</template>

<style scoped>
.contact-page {
  padding: 2rem;
  max-width: 600px;
  margin: auto;
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

input,
textarea {
  padding: 0.8rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 0.8rem;
  background: black;
  color: white;
  border: none;
  border-radius: 4px;
  font-weight: bold;
  cursor: pointer;
}

@media (max-width: 768px) {
  .contact-page {
    padding: 1rem;
  }
}
</style>
