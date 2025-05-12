<script setup lang="ts">
import { ref, onMounted } from 'vue'
import LoaderHelper from './components/LoaderHelper.vue'
import ExampleComponent from './components/ExampleComponent.vue'
import RenderItem from './components/RenderItem.vue'

const myApi = 'https://jsonplaceholder.typicode.com/posts/1'
const myApiError = 'https://google.com'

const myApiList = 'https://jsonplaceholder.typicode.com/users'

const data = ref([])
onMounted(() => {
  fetch(myApiList)
    .then((response) => response.json())
    .then((json) => {
      data.value = json
    })
    .catch((error) => {
      console.error('Error fetching data:', error)
    })
})
</script>

<template>
  <main>
    <!-- HOC (Higher-Order Component)  -->
    <!-- Consiste en una función que recibe un componente y devuelve un nuevo componente mejorado -->
    <LoaderHelper :url="myApi" :component-to-show="ExampleComponent" />
    <LoaderHelper :url="myApiError" :component-to-show="ExampleComponent" />

    <!-- Contenedor/Vizualizador -->
    <!-- Consiste en separar la lógica de negocio de la presentación visual -->
    <template v-for="(element, index) in data" :key="index">
      <RenderItem :data="element" />
    </template>
  </main>
</template>
