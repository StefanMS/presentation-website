<template>
  <div>
    <HeroSection
      title="Empowering Your Business Through Technology"
      subtitle="Digital Transformation, Data Analytics, AI Solutions, and more."
      ctaLink="/contact"
      ctaText="Get in Touch"
    />


    <MainContainer>
      <section class="py-20 bg-gray-50">
        <div class="container mx-auto px-6">
          <h2 class="text-3xl font-bold text-center mb-12">Our Services</h2>
          <div class="space-y-8">
            <div
              v-for="service in services"
              :key="service.id"
              class="bg-white rounded-lg shadow-md p-6 transition duration-300"
            >
              <!-- Service Header -->
              <div
                class="cursor-pointer flex justify-between items-center"
                @click="toggleService(service.id)"
              >
                <h3 class="text-xl font-semibold">{{ service.title }}</h3>
                <span>{{ expandedService === service.id ? '−' : '+' }}</span>
              </div>

              <!-- Expanded Tabs Section -->
              <div v-if="expandedService === service.id" class="mt-6">
                <Tabs :service="service.id" />
              </div>
            </div>
          </div>
        </div>
      </section>
    </MainContainer>

    <Footer />
  </div>
</template>

<script setup>
import HeroSection from '~/components/Layout/HeroSection.vue'
import Footer from '~/components/Layout/Footer.vue'
import MainContainer from '~/components/Layout/MainContainer.vue'
import Tabs from '~/components/Tabs.vue'

const services = [
  { id: 'digital-transformation', title: 'Digital Transformation' },
  { id: 'data-analytics', title: 'Data Analytics & Forecasting' },
  { id: 'ai-ml', title: 'AI & Machine Learning' },
  { id: 'custom-websites', title: 'Custom Websites' },
  { id: 'geospatial', title: 'Geospatial Solutions' }
]

const expandedService = ref(null)

function toggleService(id) {
  expandedService.value = expandedService.value === id ? null : id
}
</script>
