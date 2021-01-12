<template>
  <swiper>
      <swiper-item :key="item.index" v-for="item in banners">
         <a :href="item.link"></a>
        <img :src="item.image" alt="">
      </swiper-item>
    </swiper>
</template>

<script>
import {Swiper, SwiperItem} from 'components/common/swiper'
export default {
name:"HomeSwper",
props:{
    banners:{
        type:Array,
        default(){
            return []
        }
    }
},
components:{
    Swiper,
    SwiperItem
}
}
</script>

<style>

</style>