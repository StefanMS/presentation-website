<template>
  <div>
    <div class="flex gap-4 mb-4 border-b">
      <button
        v-for="tab in tabs"
        :key="tab"
        @click="activeTab = tab"
        :class="[
          'py-2 px-4',
          activeTab === tab
            ? 'border-b-2 border-blue-600 font-semibold'
            : 'text-gray-500'
        ]"
      >
        {{ tab }}
      </button>
    </div>

    <div class="bg-gray-100 p-4 rounded">
      <component :is="currentComponent" />
    </div>
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
