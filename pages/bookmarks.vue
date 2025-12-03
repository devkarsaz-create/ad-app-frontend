<template>
  <div class="min-h-screen bg-brand-dark text-white p-4 sm:p-6">
    <header class="flex items-center justify-between mb-8">
      <h1 class="text-3xl font-bold">آگهی‌های ذخیره شده</h1>
      <button class="text-brand-gray hover:text-white transition-colors">
        <Icon name="mdi:dots-vertical" class="w-6 h-6" />
      </button>
    </header>

    <div v-if="bookmarkedAds.length > 0" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
      <AdCard v-for="ad in bookmarkedAds" :key="ad.id" :ad="ad" />
    </div>

    <div v-else class="text-center py-20 flex flex-col items-center">
        <Icon name="mdi:bookmark-off-outline" class="w-24 h-24 text-gray-600 mb-4" />
        <h2 class="text-xl font-semibold text-gray-400">هنوز آگهی ذخیره نکرده‌اید</h2>
        <p class="text-gray-500 mt-2">آگهی‌های مورد علاقه خود را برای دسترسی آسان‌تر، ذخیره کنید.</p>
        <NuxtLink to="/" class="mt-6 bg-brand-blue text-white font-bold py-2 px-5 rounded-lg hover:bg-opacity-90 transition-all">
            مشاهده آگهی‌ها
        </NuxtLink>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';

// Mock data for bookmarked ads - replace with real data later
const bookmarkedAds = ref([
    {
    id: 1,
    title: 'ویلا لوکس استخردار در شمال',
    image: '/images/house-1.jpg',
    location: 'رامسر، مازندران',
    price: '۴,۵۰۰,۰۰۰,۰۰۰',
    bookmarked: true,
  },
  {
    id: 3,
    title: 'آپارتمان مدرن در مرکز تهران',
    image: '/images/house-3.jpg',
    location: 'ونک، تهران',
    price: '۱۲,۰۰۰,۰۰۰,۰۰۰',
    bookmarked: true,
  },
]);

</script>
