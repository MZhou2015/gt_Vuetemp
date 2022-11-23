<template>
  <div class="category">
    <div>Home >> Products >> Microphone</div>
    <div class="listview">
      <div class="imgx" v-for="(mx,idx) in viewlist" :key=idx >
        <img :src=img_url+mx.image >
        <p><a :href=link_url+mx.ptcode>{{mx.brief}}</a></p>
        <p>{{mx.model}}</p>
       </div>
      <div class="imgx"></div>
      <div class="imgx"></div>
      <div class="imgx"></div>
    </div> <!--    End of listView-->
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'proCategory',
  data () {
    return {
      msg: 'Welcome to Navigation Bar',
      rooturl: 'http',
      catid: 204,
      img_url: 'https://mzhou2015.github.io/gecon_pub/src/vxdagi/image/',
      link_url: '/?subfold=prodetail&pcode=',
      mddata: 'Yes',
      viewlist: [{brief: 'XiBon Power Amplifier', image: 'HK900-220619f9c.jpg', model: 'BK-300MK', ptcode: 'E30215'}]
    }
  },
  created () {
    this.rootcheck('check')
    this.getProdata(this.catid)
  },
  computed: {
    catltem: function () {
      var sd = this.mddata
      return sd
    }
  },
  methods: {
    rootcheck (context, rt) {
      var urlstring = window.location.href
      var url3 = new URL(urlstring)
      console.log('url3', url3)
      this.rooturl = url3.origin
      if (url3.host === 'localhost:3037') this.rooturl = 'http://localhost:5000'
      console.log(url3.host)
      console.log(urlstring)
      console.log(this.rooturl)
      let pcode = url3.searchParams.get('pcode')
      let subfold = url3.searchParams.get('subfold')
      if (pcode) this.catid = pcode
      console.log(pcode, subfold)
      // var root = './php/'
      // if (url3.host === 'localhost:3000') root = 'http://localhost/phptutorial/vsMain21/php/'
    },
    async getProdata (mcat) {
      // const headers = { 'Content-Type': 'application/json' }
      const furl = this.rooturl + '/gsapi/data/?subfold=category&pcode=' + mcat
      console.log(furl)
      const result = await axios.get(furl)
      this.viewlist = result.data
      console.log(result.data)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.category{
  background-color: #f6f6e5;
}
.listview{
  display: flex;
  width: 100%;
  justify-content:start;
  flex-wrap: wrap;
}
.imgx{
  width:420px;
  min-width: 360px;
  max-width: 650;
  flex-grow: 1;
  padding: 5px;
  margin: 5px;
  background-color: #f2f2f2;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.6);
  }
  .imgx p{
    width: 100%;
    height: 30px;
    font-size: 18px;
    text-align: center;
    background-color: #f2f2f2;
  }
  .imgx p a{
    color:#35459a;
    text-decoration: none;
    font-size: 20px;
  }
  img{
    width: 100%;
  }
</style>
