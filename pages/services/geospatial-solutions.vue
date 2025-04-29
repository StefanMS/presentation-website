<template>
    <section class="py-20 bg-gray-50 min-h-screen">
      <div class="container mx-auto px-6">
        <h1 class="text-3xl font-bold mb-8">Geospatial Solutions</h1>
        <Tabs :tabs="tabs" />
      </div>
    </section>
  </template>
  
  <script setup>
  import Tabs from '~/components/Tabs.vue'
  
  // Import tab components specific to this service
  import Overview from '~/components/ServiceTabs/GeospatialSolutions/Overview.vue'
  import Benefits from '~/components/ServiceTabs/GeospatialSolutions/Benefits.vue'
  import Technologies from '~/components/ServiceTabs/GeospatialSolutions/Technologies.vue'
  
  const tabs = [
    { title: 'Overview', component: Overview },
    { title: 'Benefits', component: Benefits },
    { title: 'Technologies', component: Technologies },
  ]
  </script>
  