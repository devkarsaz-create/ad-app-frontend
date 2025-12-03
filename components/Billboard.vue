
<template>
  <div 
    class="h-[40vh] md:h-[50vh] rounded-2xl flex flex-col justify-between p-6 md:p-8 relative overflow-hidden bg-graphite-charcoal border border-white/10"
  >
    <div class="z-10">
      <h2 class="text-2xl md:text-4xl font-extrabold text-graphite-white tracking-tighter">
        {{ title }}
      </h2>
      <p class="mt-2 text-md md:text-lg text-graphite-light-gray max-w-md">
        {{ subtitle }}
      </p>
    </div>
    <div class="z-10">
      <button 
        v-if="buttonText"
        class="px-6 py-2.5 bg-graphite-white text-graphite-black font-bold rounded-full text-sm transition-transform hover:scale-105 active:scale-95"
      >
        {{ buttonText }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  title: { type: String, required: true },
  subtitle: { type: String, required: true },
  buttonText: { type: String, default: '' },
});
</script>

<style scoped>
/* No specific scoped styles needed, leveraging Tailwind */
</style>
