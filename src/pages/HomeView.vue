<template>
  <div class="p-4">
    Home
  </div>
  <pre>
    {{ episodes }}
  </pre>
</template>

<script setup>
import axios from 'axios';

const episodes = ref([])

async function handleGetEpsodes(){
  try {
    const response = await axios.get('https://rickandmortyapi.com/api/episode')
    episodes.value = response.data.results
  } catch (error) {
    console.error( error)
  }
}

onMounted(() => {
  handleGetEpsodes()
})
</script>
