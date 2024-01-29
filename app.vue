<!-- pages/index.vue -->
<template>
  <div>
    <h1>Disney Characters</h1>
    <ul>
      <li v-for="character in characters" :key="character.id">{{ character.name }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useFetch } from '@nuxt/http-client'; // Change this line

const characters = ref([]);

// Fetch data from the API
onMounted(async () => {
  const { data } = await useFetch('/api/disney');
  characters.value = data;
});
</script>