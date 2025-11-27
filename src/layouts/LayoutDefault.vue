<template>
  <div class="h-screen">
      <NavBar />
      <RouterView />
  </div>
</template>

<script setup>
import NavBar from '@/components/NavBar.vue';
import { RouterView } from 'vue-router'
</script>
