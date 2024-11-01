<script setup>
import { onMounted, onUnmounted } from 'vue';
import Bio from './components/Bio.vue';
import Info from './components/Info.vue';

// Lifecycle hooks to handle scroll behavior
onMounted(() => {
  // Add scroll event listener to handle any custom scroll behavior if needed
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  // Clean up event listener on component unmount
  window.removeEventListener('scroll', handleScroll);
});

// Scroll handler function for any future scroll-based interactions
const handleScroll = () => {
  // Can be used to add additional scroll-based behaviors
  // Currently kept for extensibility
};
</script>

<template>
  <div class="container">
    <!-- Main app wrapper with responsive max-width -->
    <div class="app">
      <!-- Two-column layout wrapper -->
      <div class="layout-wrapper">
        <!-- Fixed Bio section -->
        <div class="bio-wrapper">
          <Bio 
            class="bio section" 
            msg="Bio section"
            @error="(e) => console.error('Bio component error:', e)"
          />
        </div>
        
        <!-- Scrollable Info section -->
        <div class="info-wrapper">
          <Info 
            class="info section" 
            msg="Vite + Vue"
            @error="(e) => console.error('Info component error:', e)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Container styles */
.container {
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
}

/* Main app wrapper styles */
.app {
  width: 100%;
  max-width: 1600px;
  padding: 4rem; /* 32px - using rem for better accessibility */
  margin: 0 auto;
}

/* Layout wrapper for two-column design */
.layout-wrapper {
  display: flex;
  gap: 2rem; /* Space between columns */
  position: relative;

}

/* Bio section wrapper styles */
.bio-wrapper {
  position: sticky;
  top: 4rem; /* 64px from top */
  width: 40%; /* Adjust width as needed */
  max-height: calc(100vh - 8rem); /* Viewport height minus top and bottom margins */
  overflow-y: auto; /* Allow scrolling if bio content is too long */
}

/* Info section wrapper styles */
.info-wrapper {
  flex: 1; /* Takes remaining space */
  min-height: 60%;
  min-width: 60%; /* Adjust width as needed */
  overflow-y: auto; /* Enable scrolling for info section */
}

/* Ensure sections fill their containers */
.section {
  width: 100%;
}

/* Media query for responsive design */
@media (max-width: 768px) {
  .layout-wrapper {
    flex-direction: column;
    gap: 1rem;
  }

  .bio-wrapper,
  .info-wrapper {
    width: 100%;
    position: relative;
    top: 0;
  }

  .bio-wrapper {
    max-height: none;
  }
}
</style>