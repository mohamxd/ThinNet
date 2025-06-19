<template>
  <div class="container">
    <h2>Parameters</h2>
    <label>Threshold: <input type="number" v-model.number="threshold" /></label>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const threshold = ref(0.5);
</script>

<style scoped>
.container { display: flex; flex-direction: column; gap: 1rem; }
input { width: 100%; }
</style>