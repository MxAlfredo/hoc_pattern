<!-- This is just an styled component -->
<script lang="ts" setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
})
const { data } = props
</script>

<template>
  <div v-if="data">
    <pre>{{ data }}</pre>
  </div>
</template>

<style scoped>
pre {
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 5px;
}
div {
  margin: 10px 0;
}
</style>
