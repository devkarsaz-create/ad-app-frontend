<template>
  <div class="scroll-container h-screen snap-y snap-mandatory overflow-y-scroll">
    <!-- Page 1: Hero Billboard -->
    <section class="h-screen snap-start flex items-center justify-center">
      <HeroBillboard />
    </section>

    <!-- Page 2: Ad Grid -->
    <section class="h-screen snap-start flex flex-col pt-12 bg-black">
      <!-- Header -->
      <div class="flex-shrink-0 px-4">
        <h2 class="text-2xl font-bold text-center">آخرین آگهی‌ها</h2>
        
        <!-- Category Filter -->
        <CategoryFilter class="mt-4 mb-2" @filter-change="updateCategory" />
      </div>

      <!-- Ad Grid -->
      <div class="flex-grow overflow-y-auto ad-grid-container p-4">
        <!-- Loading State -->
        <div v-if="isLoading" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6 gap-3">
          <AdCardSkeleton v-for="n in 20" :key="`skeleton-${n}`" />
        </div>

        <!-- Empty State -->
        <EmptyState v-else-if="!filteredAds.length" />

        <!-- Actual Ad Grid -->
        <div v-else class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6 gap-3">
          <AdCard v-for="ad in filteredAds" :key="ad.id" :ad="ad" />
        </div>

        <!-- Scroll Indicator (Level 4) -->
        <div v-if="!isLoading && filteredAds.length" class="text-center py-8">
          <p class="text-brand-gray animate-pulse">برای مشاهده بیشتر، اسکرول کنید</p>
        </div>

      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import HeroBillboard from '~/components/HeroBillboard.vue';
import AdCard from '~/components/AdCard.vue';
import AdCardSkeleton from '~/components/AdCardSkeleton.vue';
import CategoryFilter from '~/components/CategoryFilter.vue';
import EmptyState from '~/components/EmptyState.vue';

useHead({
  title: 'پروژه گرافیت - هزاران آگهی در یک قاب مدرن',
  meta: [
    { name: 'description', content: 'جدیدترین آگهی‌های املاک، خودرو، لوازم الکترونیکی و استخدام را در پلتفرم مدرن گرافیت پیدا کنید. سریع، زیبا و بهینه.' },
    { name: 'keywords', content: 'آگهی, خرید و فروش, گرافیت, املاک, خودرو, استخدام, مدرن' }
  ]
});

const allAds = ref([]);
const isLoading = ref(true);
const activeCategory = ref('all');

const updateCategory = (categoryId) => {
  activeCategory.value = categoryId;
};

const filteredAds = computed(() => {
  if (activeCategory.value === 'all') {
    return allAds.value;
  }
  return allAds.value.filter(ad => ad.category === activeCategory.value);
});

// Simulate data fetching
onMounted(() => {
  setTimeout(() => {
    const categories = ['real-estate', 'vehicles', 'electronics', 'home-goods', 'services'];
    allAds.value = Array.from({ length: 40 }, (_, i) => ({
      id: i + 1,
      title: `آگهی شماره ${i + 1}`,
      price: `${(Math.floor(Math.random() * 500) + 50) * 100000} تومان`,
      location: 'تهران',
      image: `https://picsum.photos/seed/${i+1}/300/200`,
      isFeatured: Math.random() < 0.15,
      category: categories[Math.floor(Math.random() * categories.length)]
    }));
    isLoading.value = false;
  }, 2000);
});

</script>

<style scoped>
.scroll-container::-webkit-scrollbar {
  width: 0px;
  background: transparent;
}

.ad-grid-container::-webkit-scrollbar {
  width: 4px;
}

.ad-grid-container::-webkit-scrollbar-thumb {
  background: #0A84FF; /* brand-blue */
  border-radius: 4px;
}
</style>
