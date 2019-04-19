<template>
  <div class="icons">
    <swiper :options="swiperOption" ref="mySwiper">
      <swiper-slide v-for="(page,index) in pages" :key="index">
        <div v-for="item in page" :key="item.id" class="icon">
          <div class="icon-img">
            <img class="img-content" :src="item.url">
          </div>
          <p class="icon-desc">{{item.title}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
    <!--<div class="swiper-pagination" slot="pagination"></div>-->
  </div>

</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      list: [{
        id: '001',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        title: '热门景点热门热门'
      }, {
        id: '002',
        url: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/f0f00d6dfe038c044dbc9a437f58b0eb.png',
        title: '一日游'
      }, {
        id: '003',
        url: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
        title: '必游'
      }, {
        id: '004',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png',
        title: '遛娃'
      }, {
        id: '005',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png',
        title: '东方明珠'
      }, {
        id: '006',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png',
        title: '世博会'
      }, {
        id: '007',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/fa/2548667cb6e902.png',
        title: '陆家嘴'
      }, {
        id: '008',
        url: 'https://img1.qunarzz.com/piao/fusion/1810/50/26ffa31b56646402.png',
        title: '赏花'
      }, {
        id: '009',
        url: 'http://img1.qunarzz.com/piao/fusion/1803/de/f26be47a6bf02a02.png',
        title: '迪士尼'
      }]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  @import "../../../../src/assets/style/mixins.styl"
  .icons >>> .swiper-container
    overflow inherit
   >>> .swiper-pagination-bullet
     height 6px
     width 6px
  >>> .swiper-pagination-bullet-active
    background-color #33BFCB
  .icons
    /*height 0*/
    width 100%
    /*padding-bottom 50%*/
    /*overflow hidden*/
    .icon
      width 25%
      /*height 0*/
      float left
      /*background-color red*/
      padding-bottom 25%
      /*overflow hidden*/
      position relative
      .icon-img
        top 0
        left 0
        right 0
        bottom 1.2rem
        position absolute
        /*background-color blue*/
        box-sizing border-box
        padding .1rem

        .img-content
          display block
          margin 0 auto
          height 100%

      .icon-desc
        position absolute
        left 0
        right 0
        bottom 0
        height 1.2rem
        line-height 1.2rem
        text-align center
        color $darkTextColor
        ellipse()
    .swiper-pagination
        bottom -1rem
        color red
</style>
