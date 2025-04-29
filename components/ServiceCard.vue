<template>
    <NuxtLink :to="link" class="block p-6 bg-white rounded-lg shadow hover:shadow-md transition">
      <h3 class="text-xl font-semibold mb-2">{{ title }}</h3>
      <p class="text-gray-600">Learn more →</p>
    </NuxtLink>
  </template>
  
  <script setup>
  defineProps({
    title: String,
    link: String
  })
  </script>
  