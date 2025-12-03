<template>
  <div class="bg-brand-graphite p-6 rounded-xl border border-gray-800 flex items-center gap-4 shadow-lg hover:shadow-brand-blue/20 hover:-translate-y-1 transition-all duration-300">
    <div class="p-3 rounded-lg" :class="iconBgColor">
      <Icon :name="icon" class="w-7 h-7 text-white" />
    </div>
    <div>
      <p class="text-sm text-brand-gray font-medium">{{ title }}</p>
      <p class="text-2xl font-bold text-white">{{ value }}</p>
    </div>
  </div>
</template>

<script setup>
  defineProps({
    icon: { type: String, required: true },
    title: { type: String, required: true },
    value: { type: [String, Number], required: true },
    iconBgColor: { type: String, default: 'bg-gray-700' }
  });
</script>
