<template>
    <div class="contact-page">
      <h1>Contact Me</h1>
      <form @submit.prevent="submitForm" action="https://formspree.io/f/xyzeljpr" method="POST">
        <label>
          Name
          <input type="text" name="name" required />
        </label>
  
        <label>
          Email
          <input type="email" name="email" required />
        </label>
  
        <label>
          Message
          <textarea name="message" rows="5" required></textarea>
        </label>
  
        <button type="submit">Send Message</button>
      </form>
    </div>
  </template>
  
  <script setup>
  function submitForm(e) {
    // This is just to avoid reload on manual testing
    console.log('Form submitted (fake handler for dev preview)')
  }
  </script>
  
  <style scoped>
  .contact-page {
    padding: 3rem 4rem;
    font-family: 'Inter', sans-serif;
    color: inherit;
    min-height: 100vh;
    box-sizing: border-box;
  }
  
  h1 {
    font-size: 2.5rem;
    font-weight: 600;
    text-align: center;
    margin-bottom: 2rem;
  }
  
  form {
    max-width: 600px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  
  label {
    display: flex;
    flex-direction: column;
    font-size: 1rem;
  }
  
  input,
  textarea {
    margin-top: 0.5rem;
    padding: 0.75rem;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 1rem;
    background: transparent;
    color: inherit;
  }
  
  button {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    font-weight: 600;
    border: none;
    background-color: #333;
    color: white;
    border-radius: 6px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  button:hover {
    background-color: #000;
  }
  </style>
  