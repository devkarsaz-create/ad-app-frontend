<template>
  <div class="flex items-center justify-center w-full px-4 sm:px-12 mb-12">
    <div v-for="(step, index) in steps" :key="step.id" class="flex items-center w-full">
      <div class="flex flex-col items-center z-10">
        <div 
          class="w-12 h-12 rounded-full flex items-center justify-center text-lg font-bold transition-all duration-300"
          :class="{
            'bg-brand-blue text-white shadow-lg shadow-brand-blue/30 scale-110': currentStep >= step.id,
            'bg-brand-graphite border-2 border-gray-700 text-brand-gray': currentStep < step.id
          }"
        >
          <Icon v-if="currentStep > step.id" name="mdi:check" class="w-7 h-7"/>
          <span v-else>{{ step.id }}</span>
        </div>
        <p class="mt-3 text-xs sm:text-sm text-center font-semibold transition-colors duration-300" :class="currentStep >= step.id ? 'text-white' : 'text-brand-gray'">{{ step.name }}</p>
      </div>
      
      <!-- Connecting line -->
      <div v-if="index < steps.length - 1" class="flex-auto h-1 transition-colors duration-500 mx-2"
           :class="currentStep > step.id ? 'bg-brand-blue' : 'bg-gray-700' ">
      </div>

    </div>
  </div>
</template>

<script setup>
  defineProps({
    steps: { type: Array, required: true },
    currentStep: { type: Number, required: true }
  });
</script>
