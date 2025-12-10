<template>
  <div class="p-4">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <CardBase
        v-for="episode in episodes"
        :key="episode.id"
        :name="episode.name"
        :episode="episode.episode"
        :air-date="episode.air_date"
        :characters="episode.characters"
      />
    </div>
    <pre>
    {{ episodes }}
  </pre>
  </div>
</template>

<script setup>
import axios from 'axios';

const episodes = ref([])

async function handleGetEpsodes() {
  try {
    const response = await axios.get('https://rickandmortyapi.com/api/episode')
    episodes.value = response.data.results
  } catch (error) {
    console.error(error)
  }
}

onMounted(() => {
  handleGetEpsodes()
})
</script>
