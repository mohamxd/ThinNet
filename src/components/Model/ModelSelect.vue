<template>
  <div class="container">
    <h2>Select Model</h2>
    <select v-model="selectedId">
      <option v-for="m in models" :key="m.id" :value="m.id">{{ m.name }}</option>
    </select>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import api from '../../services/api';
const models = ref([]);
const selectedId = ref(null);
onMounted(async () => { models.value = (await api.listModels()).data; });
</script>

<style scoped>
.container { display: flex; flex-direction: column; gap: 1rem; }
select { width: 100%; }
</style>