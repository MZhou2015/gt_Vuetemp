<template>
  <div class="category">
    <div>Home >> Products >> Microphone</div>
    <div class="listview">
      <div class="imgx" v-for="(mx,idx) in viewlist" :key=idx >
        <img :src=img_url+mx.image >
        <p><a :href=link_url+mx.ptcode>{{mx.brief}}</a></p>
        <p>{{mx.model}}</p>
        <div>{{mddata}}</div>
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
      link_url: './prodetail/',
      mddata: 'Yes',
      viewlist: [
        {brief: 'XiBon Power Amplifier', image: 'HK900-220619f9c.jpg', model: 'BK-300MK', ptcode: 'E30215'},
        {brief: 'InAndon Karaoke Player ,4T HDD with 98K songs, huge cloud songs download. Newest model (KV-V5 Max)', image: 'HK900-220619f9c.jpg', model: 'KV-815X5-4TB', ptcode: 'E30515'},
        {brief: 'XiBonKK Power Amplifier', image: 'HK900-220619f9c.jpg', model: 'BK-x300MK', ptcode: 'E30415'},
        5654, 698, 6542, 23, 98]
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
      this.rooturl = 'https://' + url3.host
      if (url3.host === 'localhost:5000') this.rooturl = 'http://' + url3.host
      console.log(url3.host)
      console.log(urlstring)
      console.log(this.rooturl)
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
        .catch((err) => {
          console.log(err)
          this.mddata = this.viewlist
          console.log(this.mddata)
        })

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
