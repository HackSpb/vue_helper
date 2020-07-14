<template>
  <div id="app">
    <img alt="Vue logo" width="100px" src="./assets/logo.png">
    <Troubles msg="Specify your problem:"/>
  </div>
</template>

<script>
import Troubles from './components/troubles.vue'

export default {
  name: 'App',
  components: {
    Troubles
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
