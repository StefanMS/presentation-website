<template>
    <div>
      <Header /> <!-- optional if you have a top nav -->
      <slot />
      <Footer />
    </div>
  </template>
  
  <script setup>
  import Footer from '~/components/layout/Footer.vue'
  </script>
  