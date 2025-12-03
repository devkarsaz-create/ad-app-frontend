<template>
  <div class="min-h-screen bg-brand-dark text-white p-4 sm:p-6 flex flex-col">
    <header class="flex items-center justify-between mb-8">
      <h1 class="text-3xl font-bold">صندوق پیام</h1>
      <button class="text-brand-gray hover:text-white transition-colors">
        <Icon name="mdi:magnify" class="w-6 h-6" />
      </button>
    </header>

    <div class="flex-grow flex items-center justify-center">
        <div class="text-center py-20 flex flex-col items-center">
            <Icon name="mdi:chat-remove-outline" class="w-24 h-24 text-gray-600 mb-4" />
            <h2 class="text-xl font-semibold text-gray-400">صندوق پیام شما خالی است</h2>
            <p class="text-gray-500 mt-2">وقتی با فروشندگان یا خریداران صحبت کنید، پیام‌هایتان اینجا نمایش داده می‌شود.</p>
        </div>
    </div>

  </div>
</template>

<script setup>
// Chat logic and message list will be implemented here later.
</script>
