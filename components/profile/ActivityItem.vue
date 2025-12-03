<template>
  <div class="flex items-center gap-4 py-4 px-2 rounded-lg hover:bg-white/5 transition-colors">
    <div class="p-3 rounded-full bg-gray-700">
      <Icon :name="icon" class="w-6 h-6" :class="iconClass"/>
    </div>
    <div class="flex-grow">
        <p class="text-white">{{ title }}</p>
        <p class="text-xs text-brand-gray">{{ description }}</p>
    </div>
    <time class="text-xs text-brand-gray self-start">{{ time }}</time>
  </div>
</template>

<script setup>
  defineProps({
      icon: { type: String, required: true },
      iconClass: { type: String, default: 'text-green-400' },
      title: { type: String, required: true },
      description: { type: String, required: true },
      time: { type: String, required: true },
  });
</script>
