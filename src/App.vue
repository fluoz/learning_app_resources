<template>
  <the-header></the-header>
  <div class="max-w-3xl h-24 mt-12 shadow-card flex items-center">
    <the-btn></the-btn>
  </div>
</template>

<script setup>
import TheHeader from "./components/TheHeader.vue";
import TheBtn from "./components/TheBtn.vue";
</script>
<style>
.shadow-card {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 2rem auto;
  max-width: 40rem;
  padding: 1rem;
  border-radius: 12px;
}

html {
  font-family: sans-serif;
}
</style>
