<template>
    <div class="home">
      <component :is="compname" />
    </div>
</template>

<script>
import proCatagory from './proCatagory'

export default {
  name: 'Home',
  components: {
    proCatagory
  },
  data () {
    return {
      compname: 'proCatagory'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
