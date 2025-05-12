<script lang="ts" setup>
import { ref, onMounted } from 'vue'
const props = defineProps({
  url: {
    type: String,
    required: true,
  },
  componentToShow: {
    type: Object,
    required: true,
  },
})
const { url, componentToShow } = props

const data = ref(null)
const error = ref(null)
const loading = ref(true)
const fetchData = async () => {
  try {
    const response = await fetch(url)
    if (!response.ok) {
      throw new Error('Network response was not ok')
    }
    data.value = await response.json()
  } catch (err) {
    error.value = err
  } finally {
    loading.value = false
  }
}
onMounted(() => {
  fetchData()
})
</script>
<template>
  <div>
    <div v-if="loading">Loading...</div>
    <div v-else-if="error">Error: {{ error.message }}</div>
    <component v-else :is="componentToShow" :data="data" />
  </div>
</template>
