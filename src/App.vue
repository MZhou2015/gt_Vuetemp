<template>
  <div id="app">
    <img src="./assets/store_logo.png">
    <navBar/>
    <Home ></Home>
    <!-- <router-view/>  -->
    <footer>Copyright © 2022 Gecon Technology Ltd.    All Rights Reserved</footer>
  </div>
</template>

<script>
import './assets/globalStyle.css'
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
footer{
    background-color: #5e6472;
    width: 100%;
    height: 80px;
    text-align: center;
    font-size: 20px;
    color: snow;
    padding-top: 12px;
    margin-top: 12px;
}
</style>
