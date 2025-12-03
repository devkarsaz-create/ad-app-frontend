
<template>
  <div class="mt-6 md:mt-8">
    <h3 class="text-lg font-bold text-graphite-light-gray tracking-tight px-1">آگهی های ویژه</h3>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3 md:gap-4 mt-3">
      <AdCard v-for="ad in ads" :key="ad.title" :ad="ad" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const ads = ref([
  {
    title: 'آیفون ۱۳ پرو مکس',
    price: 'توافقی',
    location: 'تهران، پونک',
    image: 'https://images.unsplash.com/photo-1510557880182-3d4d3cba35a5?q=80&w=2070&auto=format&fit=crop'
  },
  {
    title: 'لپتاپ مک بوک ایر M1',
    price: '۳۵٬۰۰۰٬۰۰۰ تومان',
    location: 'کرج، گوهردشت',
    image: 'https://images.unsplash.com/photo-1517336714731-489689fd1ca8?q=80&w=1926&auto=format&fit=crop'
  },
  {
    title: 'پژو ۲۰۶ تیپ ۵ مدل ۹۹',
    price: '۴۵۰٬۰۰۰٬۰۰۰ تومان',
    location: 'اصفهان، مرکز شهر',
    image: 'https://images.unsplash.com/photo-1552519507-da3b142c6e3d?q=80&w=2070&auto=format&fit=crop'
  },
    {
    title: 'دوربین سونی Alpha A7 III',
    price: '۷۰٬۰۰۰٬۰۰۰ تومان',
    location: 'شیراز، معالی آباد',
    image: 'https://images.unsplash.com/photo-1512790182537-52219e2735d8?q=80&w=1974&auto=format&fit=crop'
  }
]);
</script>
