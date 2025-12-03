<template>
  <div class="p-4 sm:p-6 lg:p-8">
    <!-- Header -->
    <div class="flex flex-col sm:flex-row justify-between items-start gap-4 mb-10">
      <div>
        <h1 class="text-3xl font-bold text-white">داشبورد مدیریتی</h1>
        <p class="mt-2 text-brand-gray">خوش آمدید، اینجا مرکز فرماندهی شماست.</p>
      </div>
      <button class="flex items-center gap-2 px-6 py-3 bg-brand-blue text-white font-semibold rounded-lg shadow-lg shadow-brand-blue/30 hover:bg-blue-600 transition-all transform hover:scale-105">
        <Icon name="mdi:plus-circle-outline" class="w-6 h-6"/>
        <span>ثبت آگهی جدید</span>
      </button>
    </div>

    <!-- Stats Widgets -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 mb-10">
      <ProfileStatCard 
        icon="mdi:eye-outline" 
        title="مجموع بازدیدها" 
        value="۱۲,۴۵۰" 
        icon-bg-color="bg-blue-500/80"
      />
      <ProfileStatCard 
        icon="mdi:bookmark-outline" 
        title="ذخیره شده" 
        value="۳۴۲" 
        icon-bg-color="bg-purple-500/80"
      />
      <ProfileStatCard 
        icon="mdi:email-outline" 
        title="پیام‌های جدید" 
        value="۱۸" 
        icon-bg-color="bg-green-500/80"
      />
    </div>

    <!-- Main Content Area -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
      <!-- Left Column: Chart -->
      <div class="lg:col-span-2 bg-brand-graphite p-6 rounded-2xl border border-gray-800 shadow-xl">
        <div class="flex justify-between items-center mb-5">
          <h3 class="text-xl font-semibold text-white">تحلیل بازدید هفتگی</h3>
          <span class="text-sm text-brand-gray">۷ روز گذشته</span>
        </div>
        <div class="h-72 sm:h-80">
           <ClientOnly>
              <ProfilePerformanceChart />
           </ClientOnly>
        </div>
      </div>

      <!-- Right Column: Recent Activities -->
      <div class="bg-brand-graphite p-6 rounded-2xl border border-gray-800 shadow-xl">
        <h3 class="text-xl font-semibold text-white mb-5">فعالیت‌های اخیر</h3>
        <ul class="space-y-4">
          <li class="flex items-start gap-4">
            <div class="p-2 bg-green-500/20 rounded-full">
              <Icon name="mdi:message-text-outline" class="w-5 h-5 text-green-400"/>
            </div>
            <div>
              <p class="text-sm font-medium text-white">پیام جدید از <span class="font-bold">کاربر۱</span></p>
              <p class="text-xs text-brand-gray">برای آگهی "ویلا در شمال"</p>
            </div>
            <time class="text-xs text-gray-500 ml-auto">۵ دقیقه پیش</time>
          </li>
           <li class="flex items-start gap-4">
            <div class="p-2 bg-purple-500/20 rounded-full">
              <Icon name="mdi:bookmark-check-outline" class="w-5 h-5 text-purple-400"/>
            </div>
            <div>
              <p class="text-sm font-medium text-white">آگهی شما ذخیره شد</p>
              <p class="text-xs text-brand-gray">"لپتاپ گیمینگ ایسوس"</p>
            </div>
             <time class="text-xs text-gray-500 ml-auto">۱ ساعت پیش</time>
          </li>
           <li class="flex items-start gap-4">
            <div class="p-2 bg-blue-500/20 rounded-full">
              <Icon name="mdi:chart-timeline-variant" class="w-5 h-5 text-blue-400"/>
            </div>
            <div>
              <p class="text-sm font-medium text-white">بازدید آگهی شما <span class="font-bold">۲۰٪+</span></p>
              <p class="text-xs text-brand-gray">"آپارتمان مرکز شهر"</p>
            </div>
             <time class="text-xs text-gray-500 ml-auto">دیروز</time>
          </li>
        </ul>
      </div>
    </div>

  </div>
</template>

<script setup>

</script>

<style scoped>
/* Add any specific styles if needed */
</style>
