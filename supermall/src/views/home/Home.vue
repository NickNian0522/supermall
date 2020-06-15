<template>
  <div id="home">
    <nav-bar class = "home-nav"><div slot="center">购物车</div></nav-bar>
  </div>
</template>
<script>
import NavBar from 'supermall/src/components/common/navbar/NavBar'
import {getHomeData} from 'network/home';
export default {
  name:"Home",
  components:{
    NavBar
  },
  data() {
    return {
      banners:[],
      recommends:[]
    }
  },
  created() {
    getHomeData.then(res=>{
      console.log(res)
      //根据协议进行解析  
      this.banners = res.data.banner.list
      this.recommends = res.data.recommend.list
    })
  },
}
</script>
<style scoped>
   .home-nav {
     background-color: var(--color-tint);
     color: white;
   }
</style>
