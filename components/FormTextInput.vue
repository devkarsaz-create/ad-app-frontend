<template>
  <div>
    <label :for="id" class="block text-sm font-medium text-brand-gray mb-2">{{ label }}</label>
    <input 
      :type="type"
      :id="id"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      :placeholder="placeholder"
      class="w-full bg-gray-900/50 border-2 border-gray-700 rounded-lg px-4 py-2.5 text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-brand-blue/50 focus:border-brand-blue transition-all duration-300"
    >
  </div>
</template>

<script setup>
defineProps({
  id: { type: String, required: true },
  label: { type: String, required: true },
  modelValue: { type: [String, Number], default: '' },
  type: { type: String, default: 'text' },
  placeholder: { type: String, default: '' },
});

defineEmits(['update:modelValue']);
</script>
