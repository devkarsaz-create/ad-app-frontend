<script setup lang="ts">
import AdCard from './AdCard.vue';

// Placeholder data for the ad list.
// In a real application, this would come from an API.
const ads = [
  {
    imageUrl: 'https://via.placeholder.com/400x300/ff9800/000000?text=Car',
    title: 'Luxury Sports Car',
    price: '$85,000',
    location: 'Tehran',
  },
  {
    imageUrl: 'https://via.placeholder.com/400x300/4caf50/000000?text=Apartment',
    title: 'Modern Downtown Apartment',
    price: '$2,500/mo',
    location: 'Isfahan',
  },
  {
    imageUrl: 'https://via.placeholder.com/400x300/f44336/000000?text=Laptop',
    title: 'High-End Gaming Laptop',
    price: '$1,800',
    location: 'Shiraz',
  },
  {
    imageUrl: 'https://via.placeholder.com/400x300/2196f3/000000?text=Watch',
    title: 'Vintage Swiss Watch',
    price: '$3,200',
    location: 'Tabriz',
  },
];
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
    <AdCard
      v-for="(ad, index) in ads"
      :key="index"
      :image-url="ad.imageUrl"
      :title="ad.title"
      :price="ad.price"
      :location="ad.location"
    />
  </div>
</template>

<style scoped>
/* The grid and gap classes from Tailwind handle the responsive layout. */
</style>
