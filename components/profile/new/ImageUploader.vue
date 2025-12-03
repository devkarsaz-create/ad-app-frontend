<template>
  <div 
    ref="dropZoneRef"
    class="w-full flex flex-col items-center justify-center p-6 border-4 border-dashed rounded-2xl transition-colors duration-300"
    :class="isOverDropZone ? 'border-brand-blue bg-brand-blue/10' : 'border-gray-700 hover:border-gray-600'"
  >
    <input 
      ref="fileInputRef" 
      type="file" 
      multiple 
      accept="image/*" 
      class="hidden" 
      @change="onFileChange"
    >
    
    <div v-if="files.length === 0" class="text-center cursor-pointer" @click="openFileDialog">
      <Icon name="mdi:cloud-upload-outline" class="w-16 h-16 text-gray-500 mb-4" />
      <p class="text-white font-semibold">تصاویر را بکشید و اینجا رها کنید</p>
      <p class="text-sm text-brand-gray mt-2">یا برای انتخاب فایل کلیک کنید</p>
      <p class="text-xs text-gray-600 mt-4">فرمت‌های مجاز: JPG, PNG, WEBP (حداکثر ۵ مگابایت)</p>
    </div>

    <div v-else class="w-full">
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
        <div v-for="(file, index) in files" :key="index" class="relative group aspect-square">
          <img :src="file.url" class="w-full h-full object-cover rounded-lg shadow-md" />
          <div class="absolute inset-0 bg-black/60 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity">
            <button @click="removeFile(index)" class="p-2 bg-red-500/80 rounded-full hover:bg-red-500">
              <Icon name="mdi:trash-can-outline" class="w-6 h-6 text-white" />
            </button>
          </div>
          <div v-if="index === 0" class="absolute top-1 left-1 bg-brand-blue text-white text-xs px-2 py-0.5 rounded-full font-semibold">
            کاور
          </div>
        </div>

        <!-- Add more button -->
        <div 
          v-if="files.length > 0"
          @click="openFileDialog"
          class="flex items-center justify-center aspect-square border-2 border-dashed border-gray-600 rounded-lg cursor-pointer hover:border-brand-blue hover:bg-brand-blue/10 transition-colors"
          >
            <Icon name="mdi:plus" class="w-10 h-10 text-gray-500" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useDropZone } from '@vueuse/core';

const emit = defineEmits(['update:files']);

const files = ref([]);
const dropZoneRef = ref(null);
const fileInputRef = ref(null);

function processFiles(fileList) {
  const newFiles = Array.from(fileList)
    .filter(file => file.type.startsWith('image/'))
    .map(file => ({
      file: file,
      url: URL.createObjectURL(file)
    }));
  
  files.value.push(...newFiles);
  emit('update:files', files.value.map(f => f.file));
}

// --- Drag & Drop logic ---
const { isOverDropZone } = useDropZone(dropZoneRef, {
  onDrop: (droppedFiles) => {
    processFiles(droppedFiles);
  },
  // Specify data types for better browser compatibility
  dataTypes: ['image/*']
});

// --- File input logic ---
function onFileChange(event) {
  processFiles(event.target.files);
}

function openFileDialog() {
  fileInputRef.value?.click();
}

// --- File management ---
function removeFile(index) {
  // Revoke the object URL to free up memory
  URL.revokeObjectURL(files.value[index].url);
  files.value.splice(index, 1);
  emit('update:files', files.value.map(f => f.file));
}

</script>
