<template>
  <div id="home">
  <nav-bar class="home-nav">
    <div slot="center">购物街</div>
  </nav-bar>
  <home-swiper :banners="banners"/>
  <recommend-view :recommends="recommends"/>
  <feature-view/>
  </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar";
  import HomeSwiper from "./childComps/HomeSwiper";

  import {getHomeMultidata} from "network/home";
  import RecommendView from "./childComps/RecommendView";
  import FeatureView from "./childComps/FeatureView";

  export default {
    name: "Home",
    components: {FeatureView, RecommendView, HomeSwiper, NavBar},
    data(){
      return{
        banners: [],
        recommends: [],
        result:null
      }
    },
    created() {
      getHomeMultidata().then(res => {
        this.result = res.data;
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
.home-nav{
  background: var(--color-tint);
  color: white;

  position: fixed;
  top: 0;
  left:0;
  right:0;
  z-index: 10;
}
#home{
  padding-top: 44px;
}
</style>
