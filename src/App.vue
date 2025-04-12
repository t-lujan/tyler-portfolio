<template>
  <div :class="{ dark: isDark }">
    <NavBar :isDark="isDark" @toggleDark="isDark = !isDark" />
    <RouterView />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import NavBar from './components/NavBar.vue'

const isDark = ref(true)
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
</style>
