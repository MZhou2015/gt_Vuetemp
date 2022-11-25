<template>
  <div class="prod">
    <div class="container bg-dark">
      <div class="row">
        <div class="box1 col border bg-light p-3">Home >> Products >> {{proinfo.name}}</div>
      </div>
      <div class="row">
        <div class="box1 col-12 col-lg-5 col-md-12 col-sm-12 border bg-light p-3"><img :src = "img_url+ proinfo.image" ></div>
        <div class="box1 col-12 col-lg-4 col-md-7 col-sm-12 border bg-light p-3">
          <h4>{{proinfo.brief}}</h4><hr>
          <h5>Features</h5>
          <ul><li v-for ="(item, index) in features" :key="index">{{item}}</li></ul>
        </div>
        <div class="box1 col-12 col-lg-3 col-md-5 col-sm-12 border bg-light p-3">
          <div class="card" style="width: 100%">
            <div class="card-body">
               <h5 class="card-title">Product Name</h5>
                 <span class="ne">{{proinfo.name}}</span><hr>
                      <p class="card-text"><span class="md">Product model:</span> {{proinfo.model}}</p>
                      <p> The product warrenty is one year , labour and parts.</p>
                      <p>Shipping from Vancouver BC Canada</p>
                              <a href="#" class="card-link">Card link</a>
                          <a href="#" class="card-link">Another link</a>
              </div>
          </div>
            </div> <!-- end of Card  -->
      </div>
      <div class="row">
        <div class="box1 col-12 border bg-light p-3">
          <h5>Specifications</h5>
          <table style="width: 68%">
            <tr v-for ="(item, index) in  specif" :key="index"><th class="fet">{{item[0]}}</th><td>{{item[1]}}</td></tr>
          </table>
        </div>
        <div class="box1 col-12 border bg-light p-3">{{proinfo.note}}</div>
      </div>
    </div><!-- end of Container  -->
  </div><!-- end of prod  temp  -->
</template>

<script>
import axios from 'axios'

export default {
  name: 'proDtail',
  data () {
    return {
      query: {sf: 'catagory', code: 204},
      proinfo: {},
      img_url: 'https://mzhou2015.github.io/gecon_pub/src/vxdagi/image/',
      link_url: 'http://localhost:5000'
    }
  },
  created () {
    const urlStr = new URL(window.location.href)
    let subfold = urlStr.searchParams.get('subfold')
    let pcode = urlStr.searchParams.get('pcode')
    this.query = {sf: subfold, code: pcode}
    this.getProinfo(this.query)
    console.log(this.query)
  },
  computed: {
    features: function () {
      let fld = this.proinfo.description.split('xx')
      return fld
    },
    specif: function () {
      let fld = this.proinfo.specification.split('xx')
      let mf = []
      if (Array.isArray(fld)) {
        fld.forEach(element => {
          let sp = element.trim().split('yy')
          mf.push(sp)
        })
        fld = mf
      }
      return fld
    }
  },
  methods: {
    async getProinfo (mcat) {
      // const headers = { 'Content-Type': 'application/json' }
      console.log(mcat)
      const furl = this.link_url + '/gsapi/data/?subfold=' + mcat.sf + '&pcode=' + mcat.code
      console.log(furl)
      const result = await axios.get(furl)
      this.proinfo = result.data[0]
      console.log(result.data)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.prod{
    padding: 12px;
}
.title{
    font-size: 14px;
    font-weight: 550;
}
img{
  width: 100%;
 }
 h4{
  color: #232386;
 }
 h5{
  color:#a32323
  }
 .ne{
  color: #232386;
  font-weight: bold;
  font-size:16px;
  }
td{
  padding: 4px 22px;
 }
th.fet{
  margin-bottom: 2px;
  padding: 4px;
  box-shadow: 2px 4px 3px #dadada;
}
.md{
  color:#a32323
}

</style>
