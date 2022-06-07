<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <SliderBranch/>
  </div>
</template>

<script>
import SliderBranch from './components/SliderBranch.vue'

export default {
  name: 'App',
  components: {
    SliderBranch
  }
}
</script>

<style>
@import './assets/styles.css';
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
