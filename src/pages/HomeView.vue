<template>
  <div class="p-4">
    Home
  </div>

  <input v-model="text" type="text" placeholder="Type here" class="input" />
  {{ text }}
</template>

<script setup>
const text = ref('')

const textWithComputed = computed(() => text.value)
</script>
