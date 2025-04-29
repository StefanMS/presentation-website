<template>
  <div>
    <!-- Modern Tabs -->
    <div class="flex flex-wrap gap-2 mb-6">
      <button
        v-for="tab in tabs"
        :key="tab"
        @click="activeTab = tab"
        :class="[
          'py-2 px-5 rounded-full text-sm font-medium transition-all duration-300',
          activeTab === tab
            ? 'bg-blue-600 text-white shadow-md'
            : 'bg-gray-100 text-gray-600 hover:bg-blue-100 hover:text-blue-700'
        ]"
      >
        {{ tab }}
      </button>
    </div>

    <!-- Animated Panel -->
    <transition name="fade" mode="out-in">
      <div
        :key="activeTab"
        class="bg-white rounded-xl shadow-inner border border-gray-100 p-6"
      >
        <component :is="currentComponent" />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, computed, defineAsyncComponent } from 'vue'

const props = defineProps({
  service: String
})

const activeTab = ref('Overview')

const tabs = ['Overview', 'Benefits', 'Technologies']

const serviceMap = {
  'digital-transformation': {
    Overview: () => import('./ServiceTabs/DigitalTransformation/Overview.vue'),
    Benefits: () => import('./ServiceTabs/DigitalTransformation/Benefits.vue'),
    Technologies: () =>
      import('./ServiceTabs/DigitalTransformation/Technologies.vue')
  },
  'data-analytics': {
    Overview: () =>
      import('./ServiceTabs/DataAnalyticsForecasting/Overview.vue'),
    Benefits: () =>
      import('./ServiceTabs/DataAnalyticsForecasting/Benefits.vue'),
    Technologies: () =>
      import('./ServiceTabs/DataAnalyticsForecasting/Technologies.vue')
  },
  'ai-ml': {
    Overview: () => import('./ServiceTabs/AIMachineLearning/Overview.vue'),
    Benefits: () => import('./ServiceTabs/AIMachineLearning/Benefits.vue'),
    Technologies: () =>
      import('./ServiceTabs/AIMachineLearning/Technologies.vue')
  },
  'custom-websites': {
    Overview: () => import('./ServiceTabs/CustomWebsites/Overview.vue'),
    Benefits: () => import('./ServiceTabs/CustomWebsites/Benefits.vue'),
    Technologies: () => import('./ServiceTabs/CustomWebsites/Technologies.vue')
  },
  'geospatial': {
    Overview: () => import('./ServiceTabs/GeospatialSolutions/Overview.vue'),
    Benefits: () => import('./ServiceTabs/GeospatialSolutions/Benefits.vue'),
    Technologies: () =>
      import('./ServiceTabs/GeospatialSolutions/Technologies.vue')
  }
}

const currentComponent = computed(() => {
  const loader = serviceMap[props.service]?.[activeTab.value]
  return loader ? defineAsyncComponent(loader) : null
})
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(10px);
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.fade-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
