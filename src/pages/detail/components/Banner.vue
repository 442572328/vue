<template>
  <div>
    <div class="banner" @click="handleBannerClick">
        <div class="img">
        <img class="img-url" :src="bannerImg">
        <div class="img-block">
          <p class="img-title">{{sightName}}</p>
          <div class="img-count"><span class="iconfont">&#xe761;</span>{{this.gallaryImgs.length}}</div>
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary :urlList="gallaryImgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from '../../../common/gallary/Gallary'
import FadeAnimation from '../../../common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  components: {FadeAnimation, CommonGallary},
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleBannerClick: function () {
      this.showGallary = true
    },
    handleGallaryClose: function () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    width 100%
    .img
      width 100%
      position relative
      .img-url
        width 100%
      .img-block
        width 100%
        height 1.5rem
        position absolute
        left 0
        bottom 1rem
        color #eaeaea
        .img-title
          line-height 1.5rem
          float left
          margin-left .5rem
        .img-count
          line-height 1.5rem
          width 5rem
          float right
          border-radius .5rem
          text-align center
          background-color rgba(0,0,0,0.4)
          font-size .8rem
          margin-right .5rem
</style>
