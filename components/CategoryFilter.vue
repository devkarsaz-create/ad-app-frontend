<template>
  <div class="w-full overflow-x-auto py-2 category-filter-container">
    <div class="flex flex-nowrap gap-2 px-4">
      <button 
        v-for="category in categories"
        :key="category.id"
        @click="setActiveCategory(category.id)"
        :class="[
          'px-4 py-2 text-sm font-semibold rounded-full whitespace-nowrap transition-all duration-300',
          isActive(category.id) 
            ? 'bg-brand-blue text-white shadow-lg shadow-brand-blue/30' 
            : 'bg-brand-graphite text-brand-gray hover:bg-brand-gray/50 hover:text-white'
        ]">
        {{ category.name }}
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['filter-change']);

const categories = ref([
  { id: 'all', name: 'همه' },
  { id: 'real-estate', name: 'املاک' },
  { id: 'vehicles', name: 'وسایل نقلیه' },
  { id: 'electronics', name: 'لوازم الکترونیکی' },
  { id: 'home-goods', name: 'لوازم خانگی' },
  { id: 'services', name: 'خدمات' },
]);

const activeCategoryId = ref('all');

const setActiveCategory = (id) => {
  activeCategoryId.value = id;
  emit('filter-change', id);
};

const isActive = (id) => activeCategoryId.value === id;

</script>

<style scoped>
.category-filter-container::-webkit-scrollbar {
  height: 0px; /* Hides scrollbar for a cleaner look */
  background: transparent;
}
</style>
