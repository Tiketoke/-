<template>
  <div id="app">
     <home-header :seller="seller"></home-header>
      <div class="tab">
          <router-link tag="div" class="tab-item" to="/goods">
            商品
          </router-link>

        <router-link tag="div" class="tab-item" to="/ratings">
          评论
        </router-link>
        <router-link tag="div" class="tab-item" to="/seller">
          商家
        </router-link>
      </div>
    <router-view :seller="seller" keep-alive></router-view>
  </div>
</template>

<script>
  import  homeHeader from '@/components/home/homeHeader'
  import  {urlParse} from '@/common/js/util'
  import axios from 'axios'
  const ERR_OK =0;
  export default {
    data() {
      return {
        seller :{
          // id:(()=>{
          //   let queryParm = urlParse();
          //   console.log(queryParm);
          //   return queryParm.id;
          // })()
        },
      };
    },
    methods: {
      getCityInfo (){
        axios.get('/api/data.json')
          .then(this.getCityInfoSucc)
      },
      getCityInfoSucc (res) {
        res =res.data;
        if(res.ret){
          this.seller =res.seller;
        }
      }
    },
    mounted (){
      this.getCityInfo();
    },
  name: 'App',
  components:{
    homeHeader
  }
}
</script>

<style lang="stylus">
  @import "./common/stylus/mixin.styl"

  .tab
    display: flex
    width: 100%
    height: 40px
    line-height: 40px
    // border-bottom: 1px solid rgba(7, 17, 27, 0.1)
    border-1px(rgba(7, 17, 27, 0.1))
    .tab-item
      flex: 1
      text-align: center
      font-size: 14px
      color: rgb(77, 85, 93)
    .router-link-active
      color: rgb(240, 20, 20)
</style>
