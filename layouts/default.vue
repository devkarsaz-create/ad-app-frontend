<template>
  <div class="bg-brand-black text-brand-white min-h-screen font-sans">
    <slot />
    <footer class="fixed bottom-4 left-1/2 -translate-x-1/2 z-20 w-[90%] max-w-md">
      <BottomNav />
    </footer>
  </div>
</template>

<script setup>
import BottomNav from '~/components/BottomNav.vue';
</script>
