<template>
  <section class="bg-gradient-to-r from-blue-600 to-indigo-700 text-white py-28">
    <div class="container mx-auto px-6 text-center">
      <h1 class="text-5xl font-extrabold mb-6">{{ title }}</h1>
      <p class="text-xl mb-8">{{ subtitle }}</p>
      <NuxtLink
        :to="ctaLink"
        class="bg-white text-blue-700 font-semibold py-3 px-6 rounded-lg shadow-lg hover:bg-gray-100 transition duration-300"
      >
        {{ ctaText }}
      </NuxtLink>
    </div>
  </section>
</template>

<script setup>
defineProps({
  title: String,
  subtitle: String,
  ctaLink: String,
  ctaText: String,
})
</script>
