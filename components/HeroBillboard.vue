<template>
  <div class="w-full h-full flex flex-col items-center justify-center text-center p-4 bg-cover bg-center" 
       style="background-image: url('https://images.unsplash.com/photo-1516455207990-7a41ce80f7ae?fm=jpg&w=3000&auto=format&fit=crop&q=60&ixlib=rb-4.0.3');">
    
    <div class="bg-black/60 p-8 rounded-2xl backdrop-blur-md w-[90%] max-w-2xl">
      <h1 class="text-4xl md:text-6xl font-extrabold text-brand-white leading-tight">پروژه گرافیت</h1>
      <p class="text-lg md:text-xl text-brand-gray mt-4 max-w-xl mx-auto">هر آنچه نیاز دارید، در یک قاب مدرن</p>
      
      <!-- Search Bar -->
      <div class="mt-8">
        <input 
          type="text"
          placeholder="دنبال چه می‌گردید؟"
          class="w-full h-12 px-5 bg-brand-graphite/80 border-2 border-brand-gray/50 rounded-full text-brand-white placeholder-brand-gray focus:outline-none focus:ring-2 focus:ring-brand-blue focus:border-transparent transition-all duration-300"
        />
      </div>

      <!-- Hot Categories -->
      <div class="mt-6">
        <p class="text-brand-gray mb-3">دسته‌بندی‌های داغ:</p>
        <div class="flex flex-wrap items-center justify-center gap-2">
          <button v-for="category in hotCategories" :key="category"
                  class="px-4 py-2 text-sm bg-brand-graphite/70 text-brand-white rounded-full hover:bg-brand-blue hover:text-white transition-colors duration-200">
            {{ category }}
          </button>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const hotCategories = ref([
  'املاک',
  'وسایل نقلیه',
  'لوازم الکترونیکی',
  'استخدام',
  'خدمات'
]);
</script>
