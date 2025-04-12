<template>
  <div class="contact-container">
    <h1>Contact Me</h1>
    <form class="contact-form" action="mailto:tyler@example.com" method="POST" enctype="text/plain">
      <input type="text" name="name" placeholder="Your Name" required />
      <input type="email" name="email" placeholder="Your Email" required />
      <textarea name="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send</button>
    </form>
  </div>
</template>

<style scoped>
.contact-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

input,
textarea {
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

textarea {
  resize: vertical;
  min-height: 120px;
}

button {
  padding: 0.75rem;
  background: black;
  color: white;
  border: none;
  border-radius: 4px;
  font-weight: bold;
  font-size: 1rem;
  cursor: pointer;
}

@media (max-width: 768px) {
  .contact-container {
    padding: 1rem;
  }

  h1 {
    font-size: 1.5rem;
  }

  input,
  textarea {
    font-size: 0.9rem;
  }

  button {
    font-size: 1rem;
  }
}
</style>
