<template>
  <div v-if="props.params.value.data.count % 2 == 0" style="color: green">even</div>
  <div v-else style="color: red">odd</div>
</template>

<script setup>
import { toRefs, defineProps, onMounted } from 'vue'

const definePropsData = defineProps(['params'])
const props = toRefs(definePropsData)
onMounted(() => {})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
