<template>
  <div class="container auth-container">
    <h2>Sign Up</h2>
    <input v-model="email" placeholder="Email" />
    <input type="password" v-model="password" placeholder="Password" />
    <button @click="handleSignup">Create Account</button>
    <router-link to="/">Already have one?</router-link>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import api from '../../services/api';
import { useRouter } from 'vue-router';
const email = ref('');
const password = ref('');
const router = useRouter();
async function handleSignup() {
  try {
    await api.signup({ email: email.value, password: password.value });
    router.push('/upload-model');
  } catch (err) { console.error(err); }
}
</script>

<style scoped>
.auth-container { max-width: 400px; margin: auto; padding: 2rem; display: flex; flex-direction: column; gap: 1rem; }
input { width: 100%; }
</style>
