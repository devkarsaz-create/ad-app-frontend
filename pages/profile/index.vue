<template>
  <div class="p-4 sm:p-8">
    <header class="mb-10">
      <h1 class="text-4xl font-bold text-white">داشبورد</h1>
      <p class="text-brand-gray mt-2">سلام، خوش آمدید! وضعیت کلی کسب و کار خود را اینجا ببینید.</p>
    </header>

    <!-- Stats Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-10">
      <ProfileStatCard 
        icon="mdi:archive-outline"
        title="کل آگهی‌ها"
        value="12"
        iconBgColor="bg-blue-500/80"
      />
      <ProfileStatCard 
        icon="mdi:eye-outline"
        title="مجموع بازدیدها"
        value="8,450"
        iconBgColor="bg-green-500/80"
      />
      <ProfileStatCard 
        icon="mdi:message-badge-outline"
        title="پیام‌های جدید"
        value="3"
        iconBgColor="bg-purple-500/80"
      />
    </div>

    <!-- Main Content Area -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
      
      <!-- Left Column: Chart -->
      <div class="lg:col-span-2">
        <ProfileViewsChart />
      </div>

      <!-- Right Column: Recent Activities -->
      <div class="bg-brand-graphite p-6 rounded-xl border border-gray-800 shadow-lg">
        <h3 class="text-lg font-bold text-white mb-4">آخرین فعالیت‌ها</h3>
        <div class="flex flex-col divide-y divide-gray-800">
          <ProfileActivityItem 
            icon="mdi:message-text-outline" 
            iconClass="text-purple-400"
            title="پیام جدید از خریدار"
            description="در مورد «ویلا لوکس استخردار»"
            time="۵ دقیقه پیش"
          />
          <ProfileActivityItem 
            icon="mdi:star-circle-outline" 
            iconClass="text-yellow-400"
            title="نظر جدید ثبت شد"
            description="کاربر «رضا» به آگهی شما امتیاز داد."
            time="۲ ساعت پیش"
          />
          <ProfileActivityItem 
            icon="mdi:check-circle-outline" 
            iconClass="text-green-400"
            title="آگهی شما تایید شد"
            description="«آپارتمان مدرن در مرکز تهران»"
            time="۱ روز پیش"
          />
           <ProfileActivityItem 
            icon="mdi:message-text-outline" 
            iconClass="text-purple-400"
            title="پیام جدید از خریدار"
            description="در مورد «باغ ویلا در شهریار»"
            time="۳ روز پیش"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  // Later, we'll fetch this data from the backend.
</script>
