<template>
  <div class="bg-brand-graphite p-5 rounded-xl border border-gray-800 flex items-center gap-5 shadow-lg transform hover:-translate-y-1 transition-transform duration-300">
    <div class="p-3 rounded-full" :class="iconBgColor">
      <Icon :name="icon" class="w-7 h-7 text-white" />
    </div>
    <div>
      <p class="text-sm text-brand-gray font-semibold">{{ title }}</p>
      <p class="text-2xl text-white font-bold">{{ value }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  icon: String,
  title: String,
  value: String,
  iconBgColor: String,
});
</script>
