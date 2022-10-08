<template>
  <div id="app">
    <img src="./assets/store_logo.png">
    <navBar/>
    {{pjdata}}
    <proCatagory />
    <!-- <router-view/>  -->
  </div>
</template>

<script>

import navBar from './components/navBar'
import proCatagory from './components/proCatagory'

export default {
  name: 'App',
  data () {
    return {
      pjdata: 'Products Json',
      catid: 204
    }
  },
  components: {
    navBar,
    proCatagory

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
