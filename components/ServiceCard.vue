<!-- ServiceCard.vue -->
<template>
  <div class="bg-white rounded-xl shadow-md hover:shadow-lg transition-all duration-300 overflow-hidden">
    <!-- Card Header -->
    <div 
      class="p-6 cursor-pointer bg-gradient-to-r from-blue-600 to-indigo-600"
      @click="isExpanded = !isExpanded"
    >
      <div class="flex justify-between items-center">
        <h3 class="text-xl font-bold text-white">{{ title }}</h3>
        <div 
          class="w-8 h-8 flex items-center justify-center rounded-full bg-white/20 text-white transition-transform duration-300"
          :class="{ 'transform rotate-45': isExpanded }"
        >
          <span class="text-xl font-bold">+</span>
        </div>
      </div>
    </div>
    
    <!-- Card Content -->
    <div 
      class="transition-all duration-500 ease-out overflow-hidden"
      :style="{ 
        maxHeight: isExpanded ? '400px' : '0',
        opacity: isExpanded ? 1 : 0
      }"
    >
      <div class="p-6">
        <Tabs :service="serviceId" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Tabs from '~/components/Tabs.vue'

// Define props
const props = defineProps({
  title: {
    type: String,
    required: true
  },
  serviceId: {
    type: String,
    required: true
  }
})

// Local component state for expansion
const isExpanded = ref(false)
</script>
