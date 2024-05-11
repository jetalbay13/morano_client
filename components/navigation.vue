<template>
    <nav class="bg-gray-800">
      <div class="mx-auto px-4 py-2 pb-5 pt-5 flex  items-center container ">
        <nuxt-link to="/" class="text-orange-400 text-xl font-bold ">Chipi Chapa Dubi Daba</nuxt-link>
        <div class="mx-32 pl-60">
          <nuxt-link to="/" class="text-white hover:text-gray-400 px-3 py-2 rounded-md">Home</nuxt-link>
          <nuxt-link to="/athletes" class="text-white hover:text-gray-400 px-3 py-2 rounded-md">Athletes</nuxt-link>
          <nuxt-link to="/register" class="text-white hover:text-gray-400 px-3 py-2 rounded-md">Subscribe</nuxt-link>
          <nuxt-link to="/contact" class="text-white hover:text-gray-400 px-3 py-2 rounded-md">Contact</nuxt-link>
          <nuxt-link to="/about" class="text-white hover:text-gray-400 px-3 py-2 rounded-md">About</nuxt-link>
        </div>
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    // No data or methods needed for this component
  }
  </script>
  
  <style scoped>
  /* Add additional styles here if needed */
  </style>