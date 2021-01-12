<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div> </nav-bar>
    <home-swper :banners = "banners"></home-swper>
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control :titles="['流行','新款','精选']" class="tab-control"></tab-control>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwper from './childComps/HomeSwper'
import RecommendView from './childComps/RecommendView'
import FeatureView from './childComps/FeatureView'

import TabControl from 'components/content/tabControl/TabControl'
import {getHomeMultidata} from "network/home"



export default {
  name:"Home",
  components:{
  NavBar,
  HomeSwper,
  RecommendView,
  FeatureView,
  FeatureView,
  TabControl
},
data(){
  return {
    banners:[],
    recommends:[]
  }
},
created(){
  getHomeMultidata().then(res =>{
    this.banners = res.data.banner.list;
    this.recommends = res.data.recommend.list;
  })
}
}
</script>

<style>
#home{
  padding-top: 44px ;
  height: 9999px;
}
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 9;
  }
  .tab-control{
    position: sticky;
    top: 44px;
  }
</style>