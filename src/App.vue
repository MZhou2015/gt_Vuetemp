<template>
  <div id="app">
    <img src="./assets/store_logo.png">
    <navBar/>
    <Home ></Home>
    <!-- <router-view/>  -->
  </div>
</template>

<script>

import navBar from './components/navBar'
import Home from './components/home'

export default {
  name: 'App',
  components: {
    navBar,
    Home
  },
  data () {
    return {
      pjdata: 'Products Json',
      catid: 204
    }
  }
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
