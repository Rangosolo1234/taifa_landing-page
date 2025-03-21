<template>
  <div class="min-h-screen flex flex-col items-center justify-center bg-gray-900 relative overflow-hidden">
    <!-- Background World Map -->
    <div class="absolute inset-0 flex items-center justify-center opacity-40">
      <img 
        src="https://upload.wikimedia.org/wikipedia/commons/a/a0/World_map_with_points.svg" 
        alt="Dotted World Map"
        class="world-map">
    </div>

    <!-- Welcome Message -->
    <div class="relative z-10 text-center text-white p-10">
      <h1 class="text-5xl font-bold">Welcome to Our Platform</h1>
      <p class="mt-4 text-lg">Experience seamless geospatial solutions</p>
      <button class="mt-6 px-6 py-3 bg-orange-500 text-white rounded-lg hover:bg-orange-600">
        Get Started
      </button>
    </div>

    <!-- Floating Animated Dots forming "TAIFA" -->
    <div class="relative w-full flex justify-center z-0">
      <svg class="w-[700px] h-[300px]" viewBox="0 0 700 300">
        <circle v-for="(dot, index) in dots"
          :key="index"
          :cx="dot.x"
          :cy="dot.y"
          r="5"
          class="animated-dot"
          :style="{ animationDelay: `${dot.delay}s` }"
        />
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

// Define dot positions to spell "TAIFA" with smooth tracing
const dots = ref([
  // T
  { x: 50, y: 50, delay: 0.1 }, { x: 70, y: 50, delay: 0.2 }, { x: 90, y: 50, delay: 0.3 },
  { x: 70, y: 70, delay: 0.4 }, { x: 70, y: 90, delay: 0.5 }, { x: 70, y: 110, delay: 0.6 },

  // A
  { x: 150, y: 50, delay: 0.7 }, { x: 130, y: 70, delay: 0.8 }, { x: 170, y: 70, delay: 0.9 },
  { x: 120, y: 90, delay: 1.0 }, { x: 180, y: 90, delay: 1.1 }, { x: 150, y: 110, delay: 1.2 },

  // I
  { x: 250, y: 50, delay: 1.3 }, { x: 250, y: 70, delay: 1.4 }, { x: 250, y: 90, delay: 1.5 },
  { x: 250, y: 110, delay: 1.6 },

  // F
  { x: 350, y: 50, delay: 1.7 }, { x: 370, y: 50, delay: 1.8 }, { x: 390, y: 50, delay: 1.9 },
  { x: 350, y: 70, delay: 2.0 }, { x: 350, y: 90, delay: 2.1 }, { x: 370, y: 90, delay: 2.2 },

  // A
  { x: 450, y: 50, delay: 2.3 }, { x: 430, y: 70, delay: 2.4 }, { x: 470, y: 70, delay: 2.5 },
  { x: 420, y: 90, delay: 2.6 }, { x: 480, y: 90, delay: 2.7 }, { x: 450, y: 110, delay: 2.8 },
]);
</script>

<style scoped>
/* Background World Map */
.world-map {
  width: 90%;
  height: auto;
  filter: invert(45%) sepia(90%) saturate(300%) hue-rotate(10deg);
}

/* Animated Dots forming "TAIFA" */
.animated-dot {
  fill: orange;
  animation: fadeIn 5s infinite alternate ease-in-out, colorCycle 6s infinite alternate ease-in-out;
  opacity: 0;
}

/* Keyframes for smooth fading effect */
@keyframes fadeIn {
  0% { opacity: 0; }
  50% { opacity: 1; }
  100% { opacity: 0; }
}

/* Keyframes for color change */
@keyframes colorCycle {
  0% { fill: orange; }
  25% { fill: blue; }
  50% { fill: red; }
  75% { fill: purple; }
  100% { fill: orange; }
}
</style>
