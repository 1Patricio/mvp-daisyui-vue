<template>
  <div class="card bg-base-100 shadow-sm hover:bg-neutral-content hover:shadow-md cursor-pointer ">
    <div class="avatar-group -space-x-6">
      <div class="avatar" v-for="character in charactersFilter" :key="character">
        <div class="w-12">
          <img :src="getImage(character)" />
        </div>
      </div>
      <div v-if="charactersCount" class="avatar avatar-placeholder">
        <div class="bg-neutral text-neutral-content w-12">
          <span>+{{ charactersCount }}</span>
        </div>
      </div>
    </div>

    <div class="card-body">
      <h2 class="card-title">
        {{ name }}
        <div class="badge badge-secondary text-white">
          {{ episode }}
        </div>
      </h2>
      <div class="card-actions justify-end">
        <div class="badge badge-outline">{{ airDate }}</div>
      </div>
    </div>

  </div>
</template>

<script setup>

const props = defineProps({
  name: String,
  episode: String,
  airDate: String,
  characters: Array
})

const charactersFilter = computed(() => {
  if (props.characters.length > 6) {
    return props.characters.splice(0, 6)
  }
  return props.characters
})

const charactersCount = computed(() => {
  if (props.characters.length > 6) {
    const count = props.characters.length - 6
    return count
  }
  return 0
})

function getImage(url) {
  const newUrl = url.replace("https://rickandmortyapi.com/api/character/", "https://rickandmortyapi.com/api/character/avatar/")
  return `${newUrl}.jpeg`
}
</script>
