<template>
  <div class="bg-brand-graphite-dark p-6 rounded-2xl border-2 border-gray-800">
    <p v-if="!ad.title" class="text-center text-brand-gray py-20">فرم را تکمیل کنید تا پیش‌نمایش آگهی را اینجا ببینید.</p>
    <div v-else class="flex flex-col items-center justify-center gap-8">
        <AdCard :ad="ad" :is-preview="true"/>
        <div class="w-full p-4 bg-yellow-900/50 text-yellow-300 border border-yellow-700 rounded-lg text-sm">
            <p class="font-semibold">توجه:</p>
            <p class="mt-1">این یک پیش‌نمایش است. پس از کلیک بر روی دکمه "انتشار"، آگهی شما برای تایید نهایی ارسال خواهد شد.</p>
        </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  formData: {
    type: Object,
    required: true
  }
});

// Create a reactive ad object for the AdCard component
const ad = computed(() => ({
  id: 999, // Dummy ID for preview
  title: props.formData.title || 'عنوان آگهی شما',
  price: props.formData.price ? props.formData.price.toLocaleString('fa-IR') : 'توافقی',
  location: 'مکان شما',
  category: props.formData.category || 'دسته‌بندی',
  // Create a temporary URL for the first image if it exists
  cover_image_url: props.formData.images.length > 0 ? URL.createObjectURL(props.formData.images[0]) : '/img/placeholder.png',
  is_special: true, // Make it stand out in preview
}));

</script>
