<template>
  <div class="category">
    <div>Home >> Products >> Feature Products</div>
    <div class="container-fliud bg-light">
      <div class="row">
        <div class=" boxf col-12 col-lg-3 col-md-6 col-sm-12" v-for="(mx,idx) in viewlist" :key=idx >
          <div class="boxm" >
            <img :src=img_url+mx.image >
            <p><a :href=link_url+mx.ptcode>{{mx.brief}}</a></p>
            <p>{{mx.model}}</p>
          </div>
        </div>
      </div>
    </div><!--    End of container-fliud -->
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'proCategory',
  props: ['apiUrl'],
  data () {
    return {
      msg: 'Welcome to Navigation Bar',
      rooturl: 'http',
      query: {sf: 'category', code: 204},
      img_url: 'https://mzhou2015.github.io/gecon_pub/src/vxdagi/image/',
      link_url: '/?subfold=prodetail&pcode=',
      mddata: 'Yes',
      viewlist: [{brief: 'XiBon Power Amplifier', image: 'HK900-220619f9c.jpg', model: 'BK-300MK', ptcode: 'E30215'}]
    }
  },
  created () {
    this.rootcheck('check')
    this.getProdata(this.query)
    console.log(this.query)
    console.log('apiUrl:', this.apiUrl)
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
      let pcode = url3.searchParams.get('pcode')
      let subfold = url3.searchParams.get('subfold')
      if (pcode) this.query = {sf: subfold, code: pcode}
      console.log(pcode, subfold)
      // var root = './php/'
      // if (url3.host === 'localhost:3000') root = 'http://localhost/phptutorial/vsMain21/php/'
    },
    async getProdata (mcat) {
      // const headers = { 'Content-Type': 'application/json' }
      console.log(mcat)
      const furl = this.apiUrl + '/gsapi/data/?subfold=' + mcat.sf + '&pcode=' + mcat.code
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
.boxf{
    padding: 2px;
    }
.boxm{
    padding: 8px;
    margin: 0px;
    box-shadow: 0 3px 5px rgba(0, 0, 0, 0.6);
  }
.boxm p{
  margin: 18px;
}
img{
    width: 100%;
  }
</style>
