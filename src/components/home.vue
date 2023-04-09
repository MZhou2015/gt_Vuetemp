<template>
    <div class="home">
      <component :is="compname" :apiUrl= apiUrl />
    </div>
</template>

<script>
import proCatagory from './proCatagory'
import proDetail from './prodetail'
import test from './test'

export default {
  name: 'Home',
  components: {
    proCatagory,
    proDetail,
    test
  },
  data () {
    return {
      compname: 'proCatagory',
      apiUrl: 'http://localhost:5000'
    }
  },
  created () {
    const urlStr = new URL(window.location.href)
    let subfold = urlStr.searchParams.get('subfold')
    if (subfold === 'prodetail') this.compname = 'proDetail'
    if (subfold === 'test') this.compname = 'test'
    this.apiUrl = urlStr.origin
    if (urlStr.host === 'localhost:3037') this.apiUrl = 'http://localhost:5000'
    console.log(urlStr)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
