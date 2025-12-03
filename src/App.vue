<script setup lang="ts">
// This is the main application component.
// It sets up the overall layout and theme.
</script>

<template>
  <div class="bg-gray-900 text-white min-h-screen font-sans">
    
    <!-- Header -->
    <header class="bg-gray-800/50 backdrop-blur-sm shadow-lg shadow-orange-500/10 border-b border-orange-500/20 sticky top-0 z-50">
      <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
        <div class="text-2xl font-bold text-orange-500">
          Divar Ad-App
        </div>
        <div>
          <a href="#" class="text-gray-300 hover:text-orange-400 mx-3 transition-colors duration-300">Home</a>
          <a href="#" class="text-gray-300 hover:text-orange-400 mx-3 transition-colors duration-300">Profile</a>
          <a href="#" class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded-lg transition-transform duration-300 transform hover:scale-105 shadow-lg shadow-orange-600/30">
            Post Ad
          </a>
        </div>
      </nav>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto px-6 py-12">
      <h1 class="text-4xl font-extrabold text-center mb-12 text-shadow-orange">Latest Ads</h1>
      
      <!-- Placeholder for Ad List -->
      <div class="text-center p-8 bg-gray-800/30 rounded-lg border border-dashed border-gray-600">
        <p class="text-gray-400">Ad listing component will be here.</p>
      </div>

    </main>

    <!-- Footer -->
    <footer class="bg-gray-800/30 border-t border-gray-700/50 mt-16">
      <div class="container mx-auto px-6 py-6 text-center text-gray-400">
        <p>&copy; 2024 Divar Ad-App. Built with Vue.js & Go.</p>
      </div>
    </footer>

  </div>
</template>

<style scoped>
/* Adding a custom text shadow utility for the fiery effect */
.text-shadow-orange {
  text-shadow: 0 0 15px rgba(249, 115, 22, 0.5), 0 0 5px rgba(251, 146, 60, 0.7);
}

/* A subtle noise texture for a premium feel */
.bg-gray-900 {
  background-image: url('data:image/svg+xml,%3Csvg width="60" height="60" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg"%3E%3Cg fill="none" fill-rule="evenodd"%3E%3Cg fill="%232a2a2a" fill-opacity="0.1"%3E%3Cpath d="M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z"/%3E%3C/g%3E%3C/g%3E%3C/svg%3E');
}
</style>
