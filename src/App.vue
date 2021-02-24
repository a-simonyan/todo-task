<template>
  <div id="app">
    <h2>ToDo</h2>
    <to-do />
  </div>
</template>

<script>
import ToDo from '@/components/ToDo.vue'
export default {
  name: "App",
  components: {
    ToDo
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
  margin-top: 100px;
}
</style>
