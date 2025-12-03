<template>
  <div class="flex h-screen bg-black text-white">
    
    <!-- Sidebar -->
    <aside class="w-64 flex-shrink-0 bg-brand-graphite p-4 border-l border-gray-800">
      <div class="flex items-center mb-10">
        <img src="/logo.svg" alt="Graphite Logo" class="h-8 w-8 mr-2">
        <h1 class="text-xl font-bold">پنل گرافیت</h1>
      </div>
      
      <nav class="flex flex-col gap-2">
        <NuxtLink to="/profile" class="flex items-center gap-3 px-4 py-2 rounded-lg transition-colors" active-class="bg-brand-blue text-white" exact>
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" /></svg>
          <span>داشبورد</span>
        </NuxtLink>

        <NuxtLink to="/profile/ads" class="flex items-center gap-3 px-4 py-2 rounded-lg transition-colors" active-class="bg-brand-blue text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path d="M7 3a1 1 0 000 2h6a1 1 0 100-2H7zM4 7a1 1 0 011-1h10a1 1 0 110 2H5a1 1 0 01-1-1zM2 11a1 1 0 011-1h14a1 1 0 110 2H3a1 1 0 01-1-1z" /></svg>
          <span>مدیریت آگهی‌ها</span>
        </NuxtLink>

        <NuxtLink to="/profile/new" class="flex items-center gap-3 px-4 py-2 rounded-lg bg-brand-blue/20 text-brand-blue hover:bg-brand-blue hover:text-white transition-colors mt-4">
         <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" /></svg>
          <span>ثبت آگهی جدید</span>
        </NuxtLink>
      </nav>

      <div class="mt-auto">
         <NuxtLink to="/" class="flex items-center gap-3 px-4 py-2 text-brand-gray hover:text-white transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M3 3a1 1 0 00-1 1v12a1 1 0 102 0V4a1 1 0 00-1-1zm10.293 9.293a1 1 0 001.414 1.414l3-3a1 1 0 000-1.414l-3-3a1 1 0 10-1.414 1.414L14.586 9H7a1 1 0 100 2h7.586l-1.293 1.293z" clip-rule="evenodd" /></svg>
            <span>بازگشت به سایت</span>
        </NuxtLink>
      </div>

    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <NuxtPage />
    </main>

  </div>
</template>

<script setup>
// Publisher layout for the admin panel
</script>

<style scoped>
/* We can add specific styles for the publisher layout here */
.router-link-exact-active {
  background-color: #0A84FF;
  color: white;
}
</style>