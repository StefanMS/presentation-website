<template>
    <section class="py-20 bg-gray-50 min-h-screen">
      <div class="container mx-auto px-6">
        <h1 class="text-3xl font-bold mb-8">Custom Websites</h1>
        <Tabs :tabs="tabs" />
      </div>
    </section>
  </template>
  
  <script setup>
  import Tabs from '~/components/Tabs.vue'
  
  // Import tab components specific to this service
  import Overview from '~/components/ServiceTabs/CustomWebsites/Overview.vue'
  import Benefits from '~/components/ServiceTabs/CustomWebsites/Benefits.vue'
  import Technologies from '~/components/ServiceTabs/CustomWebsites/Technologies.vue'
  
  const tabs = [
    { title: 'Overview', component: Overview },
    { title: 'Benefits', component: Benefits },
    { title: 'Technologies', component: Technologies },
  ]
  </script>
  