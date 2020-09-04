<template>
  <div id="app">
    <Knowdlege/>
  </div>
</template>

<script>
import Knowdlege from './components/Knowledge.vue'

export default {
  name: 'App',
  components: {
    Knowdlege
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
