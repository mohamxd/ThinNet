<template>
  <div class="container">
    <h2>Results</h2>
    <img :src="resultImage" alt="Segmentation Result" v-if="resultImage" />
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({ resultImage: String });
</script>

<style scoped>
.container { display: flex; flex-direction: column; align-items: center; gap: 1rem; }
img { max-width: 100%; border: 1px solid #C7D3DD; }
</style>