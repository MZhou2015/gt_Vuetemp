<template>
    <div class="home">
      <component :is="compname" />
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
      compname: 'proCatagory'
    }
  },
  created () {
    const urlStr = new URL(window.location.href)
    let subfold = urlStr.searchParams.get('subfold')
    if (subfold === 'prodetail') this.compname = 'proDetail'
    if (subfold === 'test') this.compname = 'test'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
