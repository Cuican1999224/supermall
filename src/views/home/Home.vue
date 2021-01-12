<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div> </nav-bar>
    <home-swper :banners = "banners"></home-swper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwper from './childComps/HomeSwper'
import RecommendView from './childComps/RecommendView'
import {getHomeMultidata} from "network/home"



export default {
name:"Home",
components:{
  NavBar,
  HomeSwper,
  RecommendView
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
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
  }
</style>