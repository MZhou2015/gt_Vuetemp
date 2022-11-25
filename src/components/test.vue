<template>
   <div class="test">
      This is a test page.
   </div>
</template>

<script>
export default {
  name: 'test',
  data () {
    return {
      msg: 'Welcome to test page!'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.test {
    height: 32px;
    background: #edeeea;
    padding-right: 10%;
}
</style>
