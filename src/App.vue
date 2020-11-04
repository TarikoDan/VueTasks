<template>
  <div id="app">
    <img width="100" alt="Vue logo" src="./assets/logo.png">
    <Task1 msg="let's explore Vue.js !!!"/>
  </div>
</template>

<script>
import Task1 from './components/Task1.vue'

export default {
  name: 'App',
  components: {
    Task1
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
}
</style>
