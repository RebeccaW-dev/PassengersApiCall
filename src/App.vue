<template>
  <div id="app">
 <Passengers />
  </div>
</template>

<script>
import Passengers from './components/Passengers.vue'

export default {
  name: 'app',
  components: {
    Passengers
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
