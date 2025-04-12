<template>
  <div class="page-container">
    <div class="content">
      <h1>Contact Me</h1>
      <form @submit.prevent class="contact-form">
        <input type="text" placeholder="Name" required />
        <input type="email" placeholder="Email" required />
        <textarea placeholder="Message" required></textarea>
        <button type="submit">Send</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.page-container {
  padding: 2rem;
  box-sizing: border-box;
  width: 100%;
}

.content {
  max-width: 600px;
  margin: 0 auto;
}

h1 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  text-align: center;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.contact-form input,
.contact-form textarea {
  padding: 0.75rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.contact-form textarea {
  min-height: 120px;
  resize: vertical;
}

.contact-form button {
  padding: 0.75rem;
  background-color: black;
  color: white;
  font-weight: bold;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

@media (max-width: 768px) {
  .page-container {
    padding: 1rem;
  }

  h1 {
    font-size: 1.6rem;
  }

  .contact-form input,
  .contact-form textarea {
    font-size: 0.9rem;
  }
}
</style>
