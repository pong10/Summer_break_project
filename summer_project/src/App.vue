<template>
  <div id="app">
    <Defaultpage msg="MQTT Configuration app"/>
  </div>
</template>

<script>
import Defaultpage from './components/page.vue'

export default {
  name: 'App',
  components: {
    Defaultpage
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
