<template>
    <div class="category">
        Home >> Products >> Microphone
       <ul>
         <li><a href="/">Home</a></li>
         <li><a href="#">Products</a>
            <ul>
                <li><a href="products/204">Amplifier/Mixer</a></li>
                <li><a href="products/206">Karaoke Player</a></li>
                <li><a href="products/206">Microphone</a></li>
            </ul>
          </li>
          <li><a href="/about">About</a></li>
       </ul>
       {{mddata}}
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'proCategory',
  data () {
    return {
      msg: 'Welcome to Navigation Bar',
      rooturl:'http',
      catid: 204,
      mddata: 'Yes'
    }
  },
  created () {
    this.rootcheck('check')
    this.getProdata(this.catid)
  },
  methods: {
    rootcheck (context, rt) {
      var urlstring = window.location.href
      var url3 = new URL(urlstring)
      this.rooturl = 'https://' + url3
      if(url3 == 'localhost:5000') this.rooturl = 'http://'+ url3
      this.rooturl = url3
      console.log(url3.host)
      console.log(urlstring)
      // var root = './php/'
      // if (url3.host === 'localhost:3000') root = 'http://localhost/phptutorial/vsMain21/php/'
    },
    async getProdata (react) {
      // const headers = { 'Content-Type': 'application/json' }
      const furl = this.rooturl + '/gsapi/data'
      await axios.get(furl, {'Content-Type': 'application/json'})
        .then(response => response.data)
        .then(mdata => {
          console.log(mdata)
          this.mddata = mdata
        })
        .then(() => console.log(this.mddata))

      // const path = context.getters.mypath
      // const mroot = context.getters.getroot
      // var url = mroot + path + react
      //  const restt = await axios.get(url)
      // const alllist = { mostact: restt.data.mostact,
      // listcate: restt.data.cate
      // }
      // console.log(restt.data)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
