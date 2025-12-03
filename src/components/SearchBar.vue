<script setup lang="ts">
// SearchBar component with input, filter, and sort options.
</script>

<template>
  <div class="bg-gray-800/60 backdrop-blur-md p-6 rounded-lg shadow-lg shadow-black/20 border border-gray-700/50 mb-12">
    <div class="flex flex-col md:flex-row gap-4 items-center">
      
      <!-- Search Input -->
      <div class="relative flex-grow w-full md:w-auto">
        <input 
          type="text" 
          placeholder="Search for ads... (e.g., 'Red car')"
          class="w-full bg-gray-900/50 border-2 border-gray-700 rounded-lg py-3 px-4 text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-transparent transition-all duration-300 shadow-inner"
        />
        <div class="absolute right-3 top-1/2 -translate-y-1/2">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" /></svg>
        </div>
      </div>

      <!-- Sort By Dropdown -->
      <select class="w-full md:w-48 bg-gray-900/50 border-2 border-gray-700 rounded-lg py-3 px-4 text-white focus:outline-none focus:ring-2 focus:ring-orange-500 transition-all duration-300">
        <option value="latest">Sort by: Latest</option>
        <option value="price-asc">Price: Low to High</option>
        <option value="price-desc">Price: High to Low</option>
      </select>

    </div>
  </div>
</template>

<style scoped>
/* Custom styling for the select dropdown arrow */
select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  background-image: url('data:image/svg+xml;charset=US-ASCII,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20width%3D%22292.4%22%20height%3D%22292.4%22%3E%3Cpath%20fill%3D%22%239CA3AF%22%20d%3D%22M287%2069.4a17.6%2017.6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.4-12.8z%22/%3E%3C/svg%3E');
  background-repeat: no-repeat;
  background-position: right 1rem center;
  background-size: 0.8em;
}
</style>
