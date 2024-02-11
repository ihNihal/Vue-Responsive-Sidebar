<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Sidebar from "@/components/Sidebar.vue";
</script>

<template>
<div class="app">
  <Sidebar></Sidebar>
  <RouterView />
</div>


</template>

<style scoped>



button {
  cursor: pointer;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}

.app {
  display: flex;

  position: relative;

  main {
    flex: 1 1 0;
    padding: 2rem;

    @media (max-width: 1024px) {
      padding-left: 6rem;
    }
  }
}
</style>
