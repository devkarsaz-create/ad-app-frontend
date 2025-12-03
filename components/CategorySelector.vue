
<template>
  <div class="mt-6 md:mt-8">
    <h3 class="text-lg font-bold text-graphite-light-gray tracking-tight px-1">دسته بندی ها</h3>
    <div class="mt-3 flex space-x-4 space-x-reverse overflow-x-auto pb-4 -mx-4 px-4">
      <div 
        v-for="category in categories" 
        :key="category.name"
        class="flex-shrink-0 w-24 h-24 bg-graphite-charcoal rounded-xl flex flex-col items-center justify-center text-center p-2 cursor-pointer transition-transform hover:scale-105 border border-white/10"
      >
        <Icon :name="category.icon" class="text-3xl text-graphite-blue" />
        <span class="mt-2 text-xs font-medium text-graphite-light-gray">{{ category.name }}</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const categories = ref([
  { name: 'خودرو', icon: 'ph:car-bold' },
  { name: 'املاک', icon: 'ph:house-line-bold' },
  { name: 'استخدام', icon: 'ph:briefcase-bold' },
  { name: 'لوازم الکترونیکی', icon: 'ph:device-mobile-bold' },
  { name: 'خدمات', icon: 'ph:wrench-bold' },
  { name: 'وسایل شخصی', icon: 'ph:t-shirt-bold' },
  { name: 'سرگرمی', icon: 'ph:game-controller-bold' },
]);
</script>

<style scoped>
/* Custom scrollbar for horizontal category selector */
.overflow-x-auto::-webkit-scrollbar {
  height: 4px;
}
.overflow-x-auto::-webkit-scrollbar-track {
  background: transparent;
}
.overflow-x-auto::-webkit-scrollbar-thumb {
  background: #0A84FF;
  border-radius: 2px;
}
.overflow-x-auto::-webkit-scrollbar-thumb:hover {
  background: #0056b3;
}
</style>
