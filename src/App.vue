<script setup>
import Bio from './components/Bio.vue';
import Info from './components/Info.vue'
</script>

<template>
  <div class="container">
    <div class="app">
      <Bio class="bio section" msg="Bio section" />
      <Info class="info section" msg="Vite + Vue" />
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  display: flex;
  justify-content: center;
}

.app {
  display: flex;
  justify-content: space-around;
  width: 100%;
  max-width: 1600px;
  padding: 64px;
}

.bio {
  position: sticky;
}
</style>