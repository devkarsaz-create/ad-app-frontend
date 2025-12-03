<template>
  <div class="bg-brand-graphite rounded-lg overflow-hidden group relative aspect-w-1 aspect-h-1 border-2 border-transparent transition-all"
       :class="{ '!border-brand-blue shadow-lg shadow-brand-blue/30': ad.isFeatured }">
    
    <img class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500 ease-in-out" :src="ad.image" :alt="ad.title">
    
    <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/40 to-transparent"></div>

    <!-- Save Button -->
    <button @click.stop="toggleBookmark" 
            class="absolute top-2 left-2 bg-black/40 text-white rounded-full p-2 backdrop-blur-sm transition-all duration-300 -translate-x-12 opacity-0 group-hover:opacity-100 group-hover:translate-x-0 hover:bg-brand-blue">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="isBookmarked ? 'M5 5a2 2 0 012-2h10a2 2 0 012 2v16l-7-3.5L5 21V5z' : 'M5 5a2 2 0 012-2h10a2 2 0 012 2v16l-7-3.5L5 21V5z'" :fill="isBookmarked ? 'currentColor' : 'none'" />
      </svg>
    </button>

    <!-- Featured Badge -->
    <div v-if="ad.isFeatured" class="absolute top-2 right-2 bg-brand-blue/80 text-white rounded-full p-1.5 backdrop-blur-sm">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
        <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.28 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
      </svg>
    </div>

    <div class="absolute bottom-0 left-0 right-0 p-3 text-brand-white">
      <h4 class="text-sm font-bold truncate">{{ ad.title }}</h4>
      <p class="text-xs text-brand-blue font-semibold mt-1">{{ ad.price }}</p>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
  ad: Object
});

const isBookmarked = ref(false);

const toggleBookmark = () => {
  isBookmarked.value = !isBookmarked.value;
  // In a real app, we would also call an API to save this state
};
</script>
