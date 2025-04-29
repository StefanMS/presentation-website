<template>
  <div>
    <HeroSection
      title="Empowering Your Business Through Technology"
      subtitle="Transforming Data into Insight, AI Solutions, and More."
      ctaLink="/contact"
      ctaText="Get in Touch"
    />
    <MainContainer>
      <section class="py-20 bg-gradient-to-b from-blue-50 to-white">
        <div class="container mx-auto px-6">
          <h2 class="text-4xl font-bold text-center text-blue-900 mb-16">Our Services</h2>
          
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
            <ServiceCard 
              v-for="service in services" 
              :key="service.id"
              :title="service.title"
              :serviceId="service.id"
            />
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
import ServiceCard from '~/components/ServiceCard.vue'

const services = [
  { id: 'digital-transformation', title: 'Digital Transformation' },
  { id: 'data-analytics', title: 'Data Analytics & Forecasting' },
  { id: 'ai-ml', title: 'AI & Machine Learning' },
  { id: 'custom-websites', title: 'Custom Websites' },
  { id: 'geospatial', title: 'Geospatial Solutions' }
]
</script>