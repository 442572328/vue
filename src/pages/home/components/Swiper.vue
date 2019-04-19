<template>
  <div class="wrapper">
    <swiper :options="swiperOption" ref="mySwiper">
      <!-- slides -->
      <swiper-slide v-for="item in swiperList" :key="item.id">
        <img class="swiper-img" :src="item.url"/>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
      <!--<div class="swiper-button-prev" slot="button-prev"></div>-->
      <!--<div class="swiper-button-next" slot="button-next"></div>-->
      <!--<div class="swiper-scrollbar"   slot="scrollbar"></div>-->
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 3000
      },
      swiperList: [{
        id: '001',
        url: 'https://imgs.qunarzz.com/piao/fusion/1803/30/cea146e3d2eda002.jpg_890x330_f72cb574.jpg'
      }, {
        id: '002',
        url: 'https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/f4f647cf6af5205713798e2f0a80edf6.jpg_890x330_d41b95f9.jpg'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  >>> .swiper-pagination-bullet
    height 6px
    width 6px
  .wrapper >>> .swiper-pagination-bullet-active
    background-color aliceblue !important
  .wrapper
    .swiper-img
      width 100%
      overflow hidden
</style>
