<script setup lang="ts">
import LoaderHelper from './components/LoaderHelper.vue'
import ExampleComponent from './components/ExampleComponent.vue'

const myApi = 'https://jsonplaceholder.typicode.com/posts/1'
const myApiError = 'https://google.com'
</script>

<template>
  <main>
    <LoaderHelper :url="myApi" :component-to-show="ExampleComponent" />
    <LoaderHelper :url="myApiError" :component-to-show="ExampleComponent" />
  </main>
</template>
