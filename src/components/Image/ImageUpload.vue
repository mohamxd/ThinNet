<template>
  <div class="container">
    <h2>Upload Image</h2>
    <input type="file" accept="image/*" @change="onFileChange" />
  </div>
</template>

<script setup>
import { emit } from 'vue';
const file = ref(null);
function onFileChange(e) { file.value = e.target.files[0]; emit('image-selected', file.value); }
</script>

<style scoped>
.container { display: flex; flex-direction: column; gap: 1rem; }
</style>