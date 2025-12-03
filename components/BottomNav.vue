<template>
  <nav class="h-16 bg-brand-graphite/70 backdrop-blur-lg rounded-full flex items-center justify-around shadow-2xl shadow-brand-blue/20 border border-brand-gray/30">
    <NuxtLink v-for="item in navItems" :key="item.name" :to="item.path"
              class="flex flex-col items-center justify-center text-brand-gray hover:text-brand-blue transition-colors duration-200 w-1/5 rounded-full h-full" 
              active-class="text-brand-blue">
      <Icon :name="item.icon" class="w-7 h-7" />
    </NuxtLink>
  </nav>
</template>

<script setup>
import { ref } from 'vue';

const navItems = ref([
  { name: 'آگهی‌ها', icon: 'mdi:apps', path: '/' },
  { name: 'ذخیره‌ها', icon: 'mdi:bookmark-outline', path: '/bookmarks' },
  // مسیر اصلاح شد تا به ورک‌اسپیس جدید در پنل مدیریت اشاره کند
  { name: 'ثبت آگهی', icon: 'mdi:plus-circle', path: '/profile/new' },
  { name: 'چت', icon: 'mdi:message-processing-outline', path: '/chat' },
  // این مسیر به داشبورد پنل مدیریت می‌رود
  { name: 'پروفایل', icon: 'mdi:account-circle-outline', path: '/profile' },
]);
</script>

<style scoped>
/* Add a subtle glow to the active link */
.text-brand-blue {
  text-shadow: 0 0 15px theme('colors.brand-blue');
}
</style>
