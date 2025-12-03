<template>
  <button 
    class="w-full flex items-center justify-center gap-2 bg-brand-blue text-white font-bold py-3 px-6 rounded-lg shadow-lg shadow-brand-blue/30 hover:bg-opacity-90 transition-all duration-300 transform hover:scale-105">
    <slot />
    <Icon v-if="icon" :name="icon" />
  </button>
</template>

<script setup>
defineProps({ icon: String });
</script>
