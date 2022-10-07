<template>
  <div id="app">
    <img src="./assets/store_logo.png">
    <navBar/>
    <!-- <router-view/>  -->
  </div>
</template>

<script>

import navBar from './components/navBar'

export default {
  name: 'App',
  components: { navBar }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
