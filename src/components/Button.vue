<script setup lang="ts">
// A reusable button component with a fiery, glowing effect.

defineProps<{ text: string }>();
</script>

<template>
  <button
    class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-3 px-6 rounded-lg transition-all duration-300 transform hover:scale-105 shadow-lg shadow-orange-600/30 focus:outline-none focus:ring-4 focus:ring-orange-500/50"
  >
    {{ text }}
  </button>
</template>

<style scoped>
/* The shadow and ring classes from Tailwind provide the glow effect. */
/* The transition classes ensure a smooth animation on hover/focus. */
</style>
