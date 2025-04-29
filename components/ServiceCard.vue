<template>
  <div class="bg-white rounded-3xl shadow-md hover:shadow-xl transition-all duration-300 overflow-hidden border border-gray-100">
    
    <!-- Card Header -->
    <button
      class="w-full text-left p-6 bg-gradient-to-r from-blue-600 to-indigo-600 rounded-t-3xl focus:outline-none"
      @click="isExpanded = !isExpanded"
    >
      <div class="flex justify-between items-center">
        <h3 class="text-xl font-semibold text-white tracking-wide">{{ title }}</h3>
        <div 
          class="w-8 h-8 flex items-center justify-center rounded-full bg-white/20 text-white transition-all duration-300"
          :class="isExpanded ? 'rotate-45' : 'rotate-0'"
        >
          <span class="text-2xl leading-none">+</span>
        </div>
      </div>
    </button>

    <!-- Expandable Content -->
    <transition name="fade-expand">
      <div v-show="isExpanded" class="bg-white px-6 py-5">
        <Tabs :service="serviceId" />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Tabs from '~/components/Tabs.vue'

const props = defineProps({
  title: String,
  serviceId: String
})

const isExpanded = ref(false)
</script>

<style scoped>
.fade-expand-enter-active,
.fade-expand-leave-active {
  transition: max-height 0.4s ease, opacity 0.4s ease;
}
.fade-expand-enter-from,
.fade-expand-leave-to {
  max-height: 0;
  opacity: 0;
}
.fade-expand-enter-to,
.fade-expand-leave-from {
  max-height: 1000px; /* enough to accommodate content */
  opacity: 1;
}
</style>
