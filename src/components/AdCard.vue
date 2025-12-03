<script setup lang="ts">
// The AdCard component displays a single ad in a visually appealing card format.

defineProps<{
  imageUrl: string;
  title: string;
  price: string;
  location: string;
}>();
</script>

<template>
  <div class="bg-gray-800/50 rounded-lg overflow-hidden shadow-lg shadow-black/30 border border-gray-700/50 group transition-all duration-300 transform hover:scale-105 hover:shadow-orange-500/20 hover:border-orange-500/30">
    <!-- Ad Image -->
    <div class="relative h-56">
      <img :src="imageUrl" :alt="title" class="w-full h-full object-cover transition-transform duration-300 group-hover:scale-110" />
      <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
      <div class="absolute bottom-0 left-0 p-4">
        <h3 class="text-2xl font-bold text-white text-shadow-orange">{{ title }}</h3>
      </div>
    </div>

    <!-- Ad Info -->
    <div class="p-5">
      <div class="flex justify-between items-center mb-4">
        <p class="text-xl font-bold text-orange-500">{{ price }}</p>
        <p class="text-sm text-gray-400">{{ location }}</p>
      </div>
      
      <p class="text-gray-300 mb-5 h-12 overflow-hidden">A brief description of the ad will go here to entice the user.</p>

      <button class="w-full bg-orange-600/90 hover:bg-orange-600 text-white font-bold py-2 px-4 rounded-lg transition-all duration-300 transform hover:scale-105 shadow-md shadow-orange-600/20 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-orange-500">
        View Details
      </button>
    </div>
  </div>
</template>

<style scoped>
.text-shadow-orange {
  text-shadow: 0 0 8px rgba(249, 115, 22, 0.6);
}
</style>
