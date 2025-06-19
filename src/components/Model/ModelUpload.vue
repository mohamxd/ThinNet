<template>
  <div class="container">
    <h2>Upload Model</h2>
    <input type="file" @change="onFileChange" />
    <button @click="upload">Upload</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import api from '../../services/api';
const file = ref(null);
function onFileChange(e) { file.value = e.target.files[0]; }
async function upload() { if (file.value) await api.uploadModel(file.value); }
</script>

<style scoped>
.container { display: flex; flex-direction: column; gap: 1rem; }
</style>