<template>
  <div id="app">
    <h1>My Calculator</h1>
    <calculator></calculator>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  components: {Calculator},
  name: 'App'
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    max-width: 900px;
    margin: 60px auto;
  }

  h1 {
    margin-bottom: 30px;
  }
</style>
