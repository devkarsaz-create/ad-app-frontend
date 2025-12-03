<template>
  <div class="p-4 sm:p-6 lg:p-8">
    <!-- Header -->
    <div class="flex flex-col sm:flex-row justify-between items-start gap-4 mb-10">
      <div>
        <h1 class="text-3xl font-bold text-white">مدیریت آگهی‌ها</h1>
        <p class="mt-2 text-brand-gray">آگهی‌های خود را ویرایش، مدیریت و بررسی کنید.</p>
      </div>
       <NuxtLink to="/profile/new" class="flex items-center gap-2 px-6 py-3 bg-brand-blue text-white font-semibold rounded-lg shadow-lg shadow-brand-blue/30 hover:bg-blue-600 transition-all transform hover:scale-105">
        <Icon name="mdi:plus-circle-outline" class="w-6 h-6"/>
        <span>ثبت آگهی جدید</span>
      </NuxtLink>
    </div>

    <!-- Ad List Table -->
    <div class="bg-brand-graphite border border-gray-800 rounded-2xl shadow-xl overflow-hidden">
      <!-- Tabs for filtering -->
      <div class="flex border-b border-gray-700 bg-brand-graphite-dark">
        <button v-for="tab in tabs" :key="tab.status" @click="activeTab = tab.status"
          :class="[
            'px-6 py-3 text-sm font-semibold transition-colors',
            activeTab === tab.status 
              ? 'text-white border-b-2 border-brand-blue'
              : 'text-brand-gray hover:text-white'
          ]">
          {{ tab.name }} ({{ ads.filter(ad => tab.status === 'all' || ad.status === tab.status).length }})
        </button>
      </div>

      <!-- Table -->
      <div class="overflow-x-auto">
        <table class="w-full text-sm text-right text-brand-gray">
          <thead class="text-xs uppercase bg-brand-graphite-dark">
            <tr>
              <th scope="col" class="px-6 py-4">عنوان آگهی</th>
              <th scope="col" class="px-6 py-4 text-center">وضعیت</th>
              <th scope="col" class="px-6 py-4 text-center">تاریخ انتشار</th>
              <th scope="col" class="px-6 py-4 text-center">عملیات</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="ad in filteredAds" :key="ad.id" class="border-b border-gray-800 hover:bg-brand-graphite-dark transition-colors">
              <th scope="row" class="px-6 py-4 font-medium text-white whitespace-nowrap">
                <div class="flex items-center gap-3">
                  <img :src="ad.coverImage || '/placeholder.png'" alt="" class="w-16 h-10 object-cover rounded-md">
                  <span>{{ ad.title }}</span>
                </div>
              </th>
              <td class="px-6 py-4 text-center">
                <span class="px-3 py-1 text-xs rounded-full" :class="statusClass(ad.status)">
                  {{ statusText(ad.status) }}
                </span>
              </td>
              <td class="px-6 py-4 text-center font-mono">{{ ad.publishedDate }}</td>
              <td class="px-6 py-4 text-center">
                <div class="flex items-center justify-center gap-2">
                  <button class="p-2 rounded-full hover:bg-gray-700 transition-colors"><Icon name="mdi:eye-outline" class="w-5 h-5 text-blue-400"/></button>
                  <button class="p-2 rounded-full hover:bg-gray-700 transition-colors"><Icon name="mdi:pencil-outline" class="w-5 h-5 text-yellow-400"/></button>
                  <button class="p-2 rounded-full hover:bg-gray-700 transition-colors"><Icon name="mdi:trash-can-outline" class="w-5 h-5 text-red-400"/></button>
                </div>
              </td>
            </tr>
            <tr v-if="filteredAds.length === 0">
                <td colspan="4" class="text-center py-12 text-brand-gray">
                    هیچ آگهی در این دسته وجود ندارد.
                </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const tabs = [
  { name: 'همه آگهی‌ها', status: 'all' },
  { name: 'فعال', status: 'active' },
  { name: 'در انتظار تایید', status: 'pending' },
  { name: 'منقضی شده', status: 'expired' },
];

const activeTab = ref('all');

// Dummy data - This will be replaced with API call
const ads = ref([
  { id: 1, title: 'ویلا مدرن استخردار در شمال', status: 'active', publishedDate: '۱۴۰۳/۰۴/۱۵', coverImage: 'https://images.unsplash.com/photo-1613490493576-7fde63acd811?w=500' },
  { id: 2, title: 'آپارتمان ۱۲۰ متری مرکز شهر', status: 'pending', publishedDate: '۱۴۰۳/۰۴/۱۴', coverImage: 'https://images.unsplash.com/photo-1580587771525-78b9dba3b914?w=500' },
  { id: 3, title: 'لپتاپ گیمینگ ROG Strix', status: 'expired', publishedDate: '۱۴۰۳/۰۲/۲۰', coverImage: 'https://images.unsplash.com/photo-1593642702821-c8da6771f0c6?w=500' },
  { id: 4, title: 'خودرو پژو ۲۰۷ مدل ۱۴۰۱', status: 'active', publishedDate: '۱۴۰۳/۰۴/۱۰', coverImage: 'https://images.unsplash.com/photo-1617469747534-b9499a99c26a?w=500' },
]);

const filteredAds = computed(() => {
  if (activeTab.value === 'all') {
    return ads.value;
  }
  return ads.value.filter(ad => ad.status === activeTab.value);
});

const statusClass = (status) => {
  return {
    'bg-green-500/20 text-green-400': status === 'active',
    'bg-yellow-500/20 text-yellow-400': status === 'pending',
    'bg-red-500/20 text-red-400': status === 'expired',
  };
};

const statusText = (status) => {
    const map = {
        active: 'فعال',
        pending: 'در انتظار تایید',
        expired: 'منقضی شده',
    };
    return map[status];
}
</script>
