<template>
  <div class="container">
    <h2>Compare Two Models</h2>
    <ModelSelect v-model:selectedId="modelA" />
    <ModelSelect v-model:selectedId="modelB" />
    <ImageUpload @image-selected="setImage" />
    <button @click="runComparison">Run Comparison</button>
    <div class="compare-results" v-if="results">
      <div>
        <h3>Model A</h3>
        <img :src="results.a" alt="Result A" />
      </div>
      <div>
        <h3>Model B</h3>
        <img :src="results.b" alt="Result B" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import api from '../../services/api';
import ModelSelect from '../Model/ModelSelect.vue';
import ImageUpload from '../Image/ImageUpload.vue';

const modelA = ref(null);
const modelB = ref(null);
const image = ref(null);
const results = ref(null);

function setImage(file) { image.value = file; }

async function runComparison() {
  const form = new FormData();
  form.append('modelA', modelA.value);
  form.append('modelB', modelB.value);
  form.append('image', image.value);
  const res = await api.runSegmentation(form);
  results.value = res.data;
}
</script>

<style scoped>
.container { display: flex; flex-direction: column; gap: 1rem; }
.compare-results { display: flex; justify-content: space-around; }
img { max-width: 45%; border: 1px solid #C7D3DD; }
</style>