<template>
  <div class="p-4 sm:p-8">
    <header class="mb-10 text-center">
      <h1 class="text-4xl font-bold text-white">ثبت آگهی جدید</h1>
      <p class="text-brand-gray mt-2">یک آگهی حرفه‌ای بسازید و کسب و کار خود را رونق دهید.</p>
    </header>

    <!-- Stepper Component -->
    <ProfileNewStepper :steps="steps" :current-step="currentStep" />

    <div class="max-w-4xl mx-auto mt-16">
      <!-- Step 1: Basic Information -->
      <div v-if="currentStep === 1">
        <h2 class="text-2xl font-bold text-white mb-6">۱. اطلاعات پایه</h2>
        <form @submit.prevent="nextStep" class="space-y-6">
          <!-- Ad Title -->
          <div>
            <label for="ad-title" class="block text-sm font-medium text-brand-gray mb-2">عنوان آگهی</label>
            <input type="text" id="ad-title" v-model="formData.title" class="w-full bg-brand-graphite-dark border-2 border-gray-700 rounded-lg px-4 py-3 text-white focus:border-brand-blue focus:ring-0 transition-all" placeholder="مثال: ویلا مدرن استخردار در شمال">
          </div>

          <!-- Category & Sub-category -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <label for="category" class="block text-sm font-medium text-brand-gray mb-2">دسته‌بندی</label>
              <select id="category" v-model="formData.category" class="w-full bg-brand-graphite-dark border-2 border-gray-700 rounded-lg px-4 py-3 text-white focus:border-brand-blue focus:ring-0 transition-all">
                <option disabled value="">انتخاب کنید...</option>
                <option>املاک</option>
                <option>وسایل نقلیه</option>
                <option>کالای دیجیتال</option>
              </select>
            </div>
            <div>
              <label for="subcategory" class="block text-sm font-medium text-brand-gray mb-2">زیرمجموعه</label>
              <select id="subcategory" v-model="formData.subcategory" class="w-full bg-brand-graphite-dark border-2 border-gray-700 rounded-lg px-4 py-3 text-white focus:border-brand-blue focus:ring-0 transition-all">
                <option disabled value="">انتخاب کنید...</option>
                <option>فروش آپارتمان</option>
                <option>اجاره ویلا</option>
                <option>خودرو سواری</option>
              </select>
            </div>
          </div>

          <!-- Price -->
          <div>
            <label for="price" class="block text-sm font-medium text-brand-gray mb-2">قیمت (تومان)</label>
            <input type="number" id="price" v-model="formData.price" class="w-full bg-brand-graphite-dark border-2 border-gray-700 rounded-lg px-4 py-3 text-white focus:border-brand-blue focus:ring-0 transition-all" placeholder="مبلغ را وارد کنید">
          </div>
        </form>
      </div>

      <!-- Step 2: Details & Description -->
      <div v-if="currentStep === 2">
         <h2 class="text-2xl font-bold text-white mb-6">۲. جزئیات و توضیحات</h2>
         <p class="text-brand-gray mb-4 text-sm">توضیحات کامل و جذابی بنویسید تا شانس دیده شدن آگهی شما بیشتر شود.</p>
         <div class="bg-brand-graphite-dark border-2 border-gray-700 rounded-lg p-1 text-white focus-within:border-brand-blue transition-all">
           <EditorContent :editor="editor" />
         </div>
      </div>

      <!-- Step 3: Image Upload -->
      <div v-if="currentStep === 3">
         <h2 class="text-2xl font-bold text-white mb-6">۳. گالری تصاویر</h2>
         <p class="text-brand-gray mb-4 text-sm">حداقل یک تصویر برای کاور آگهی الزامی است. می‌توانید تصاویر را بکشید و اینجا رها کنید.</p>
         <ProfileNewImageUploader @update:files="files => formData.images = files" />
      </div>

      <!-- Step 4: Review & Publish -->
      <div v-if="currentStep === 4">
        <h2 class="text-2xl font-bold text-white mb-6">۴. بازبینی و انتشار</h2>
        <p class="text-brand-gray mb-4 text-sm">آخرین نگاه را به آگهی خود بیندازید. این همان چیزی است که کاربران می‌بینند.</p>
        <!-- Ad Preview Component will go here -->
        <div class="w-full h-96 border-2 border-gray-700 rounded-xl flex items-center justify-center">
            <p class="text-brand-gray">پیش‌نمایش زنده آگهی اینجا قرار خواهد گرفت</p>
         </div>
      </div>

      <!-- Navigation Buttons -->
      <div class="flex justify-between mt-16">
        <button @click="prevStep" :disabled="currentStep === 1" class="px-8 py-3 rounded-lg bg-brand-graphite border-2 border-gray-700 text-white font-semibold hover:bg-gray-800 disabled:opacity-50 disabled:cursor-not-allowed transition-all">
          قبلی
        </button>
        <button v-if="currentStep < steps.length" @click="nextStep" class="px-8 py-3 rounded-lg bg-brand-blue text-white font-semibold hover:bg-blue-600 transition-all shadow-lg shadow-brand-blue/20">
          بعدی
        </button>
        <button v-else @click="publishAd" class="px-8 py-3 rounded-lg bg-green-500 text-white font-semibold hover:bg-green-600 transition-all shadow-lg shadow-green-500/20">
          انتشار آگهی
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';
  import { useEditor, EditorContent } from '@tiptap/vue-3';
  import StarterKit from '@tiptap/starter-kit';

  // Stepper configuration
  const steps = ref([
    { id: 1, name: 'اطلاعات پایه' },
    { id: 2, name: 'جزئیات' },
    { id: 3, name: 'تصاویر' },
    { id: 4, name: 'انتشار' },
  ]);
  const currentStep = ref(1);

  // Form data
  const formData = reactive({
    title: '',
    category: '',
    subcategory: '',
    price: null,
    description: '',
    images: [],
  });

  // Tiptap Editor
  const editor = useEditor({
    content: '<p>اینجا شروع به نوشتن کنید...</p>',
    extensions: [StarterKit],
    editorProps: {
        attributes: {
            class: 'prose prose-invert max-w-none focus:outline-none p-4',
        },
    },
    onUpdate: ({ editor }) => {
      formData.description = editor.getHTML();
    },
  });

  // Navigation functions
  const nextStep = () => {
    if (currentStep.value < steps.value.length) {
      currentStep.value++;
    }
  };

  const prevStep = () => {
    if (currentStep.value > 1) {
      currentStep.value--;
    }
  };

  const publishAd = () => {
    // Logic to submit formData to backend
    console.log('Publishing ad:', formData);
    alert('آگهی برای انتشار ارسال شد! (اطلاعات در کنسول ثبت شده است)');
  };
</script>

<style>
/* Basic styling for Tiptap editor */
.prose:focus {
  outline: none;
}
.prose p.is-editor-empty:first-child::before {
  content: attr(data-placeholder);
  float: left;
  color: #6b7280; /* text-gray-500 */
  pointer-events: none;
  height: 0;
}
.tiptap {
    min-height: 15rem; 
}
</style>
