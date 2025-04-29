<template>
  <div>
    <HeroSection
      title="Empowering Your Business Through Technology"
      subtitle="Transforming Data into Insight, AI Solutions, and More."
      ctaLink="/contact"
      ctaText="Get in Touch"
    />
    <MainContainer>
      <section class="py-24 bg-white">
  <div class="container mx-auto px-6 lg:px-20">
    <div class="text-center mb-16">
      <h2 class="text-5xl font-extrabold text-gray-900">What We Offer</h2>
      <p class="mt-4 text-lg text-gray-600 max-w-2xl mx-auto">
        We help small businesses and bold entrepreneurs level up through powerful digital solutions built for impact, clarity, and growth.
      </p>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-10">
      <div 
        v-for="service in services" 
        :key="service.id"
        @click="toggleService(service.id)"
        class="bg-white rounded-3xl border border-gray-100 shadow-md hover:shadow-xl hover:-translate-y-1 transition-all duration-300 cursor-pointer group"
        :class="selectedService === service.id ? 'ring-2 ring-blue-500' : ''"
      >
        <div class="p-6 flex flex-col h-full">
          <div class="flex items-center justify-center w-14 h-14 rounded-full bg-blue-100 text-blue-600 text-2xl mb-4 group-hover:bg-blue-600 group-hover:text-white transition">
            <i :class="service.icon" />
          </div>

          <h3 class="text-xl font-semibold text-gray-800 group-hover:text-blue-600 transition">
            {{ service.title }}
          </h3>
          <p class="mt-3 text-gray-600 text-sm leading-relaxed">
            {{ service.shortDesc }}
          </p>
        </div>
      </div>
    </div>

    <div 
      v-if="selectedService" 
      class="mt-16 bg-white rounded-2xl shadow-lg overflow-hidden transition-all duration-500"
      :key="selectedService"
    >
      <div class="bg-gradient-to-r from-blue-600 to-indigo-600 p-6 flex justify-between items-center">
        <h3 class="text-xl font-bold text-white">
          {{ services.find(s => s.id === selectedService).title }}
        </h3>
        <button 
          @click="selectedService = null" 
          class="w-8 h-8 flex items-center justify-center rounded-full bg-white/20 text-white hover:bg-white/30 transition-all">
          ×
        </button>
      </div>
      <div class="p-6">
        <Tabs :service="selectedService" />
      </div>
    </div>
  </div>
</section>

    </MainContainer>
    <Footer />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HeroSection from '~/components/Layout/HeroSection.vue'
import Footer from '~/components/Layout/Footer.vue'
import MainContainer from '~/components/Layout/MainContainer.vue'
import Tabs from '~/components/Tabs.vue'
import '@fortawesome/fontawesome-free/css/all.min.css'


const services = [
  { 
    id: 'digital-transformation',
    title: 'Digital Transformation',
    shortDesc: 'Modernize your operations with lean, scalable technology.',
    icon: 'fas fa-sync-alt'
  },
  { 
    id: 'data-analytics',
    title: 'Data Analytics & Forecasting',
    shortDesc: 'Reveal patterns and predict the future with smart data.',
    icon: 'fas fa-chart-line'
  },
  { 
    id: 'ai-ml',
    title: 'AI & Machine Learning',
    shortDesc: 'Automate and accelerate with AI-driven innovation.',
    icon: 'fas fa-brain'
  },
  { 
    id: 'custom-websites',
    title: 'Custom Websites',
    shortDesc: 'Websites that speak your brand, responsive and blazing fast.',
    icon: 'fas fa-laptop-code'
  },
  { 
    id: 'geospatial',
    title: 'Geospatial Solutions',
    shortDesc: 'Unlock insights from spatial data and Earth observations.',
    icon: 'fas fa-globe-europe'
  }
]


const selectedService = ref(null)

function toggleService(id) {
  // If clicking the already selected service, close it
  if (selectedService.value === id) {
    selectedService.value = null
  } else {
    // Otherwise, select the new service
    selectedService.value = id
  }
}
</script>

<style scoped>
.service-card {
  height: 100%;
}
</style>