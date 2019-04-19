<template>
    <div>
      <div class="bg" @click="handleGallaryClick">
        <div class="img">
          <swiper :options="swiperOption">
            <swiper-slide v-for="(item,index) in urlList" :key="index"><img class="img-url" :src="item"></swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
          </swiper>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    urlList: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    handleGallaryClick: function () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  >>>.swiper-container
    overflow inherit
  .bg
    display flex
    flex-direction column
    justify-content center
    background-color black
    top 0
    bottom 0
    left 0
    right 0
    position fixed
    z-index 99
    .img
      height 0
      width 100%
      padding-bottom 66%
    .swiper-pagination
      bottom -7rem
      color #eee
</style>
