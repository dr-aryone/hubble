<template>
  <div id="app">
    <img alt="Vue logo" style="width: 30vh" src="https://cdn.iconscout.com/public/images/icon/free/png-512/github-logo-3a2d7bd7758f6cb1-512x512.png">
    <Home/>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'app',
  components: {
    Home
  }
}
</script>

<style>
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
