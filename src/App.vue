<template>
  <AgGridStaticId />
  <AgGridDynamicId />
</template>

<script>
import AgGridStaticId from './components/AgGridStaticId.vue'
import AgGridDynamicId from './components/AgGridDynamicId.vue'

export default {
  name: 'App',
  components: {
    AgGridStaticId,
    AgGridDynamicId
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
