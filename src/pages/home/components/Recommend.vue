<template>
  <div class="recommend">
    <div class="title">
      <div class="title-group">
        <img class="title-img" src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="本周热门榜单"><span class="title-desc">本周热门榜单</span>
        <span class="title-all"> 全部榜单></span>
      </div>
    </div>
    <div class="swiper-container">
      <swiper :options="swiperOption" ref="mySwiper">
        <swiper-slide v-for="(page,index) in pages" :key="index">
          <div class="detail">
            <div v-for="item in page" :key="item.id" class="detail-group">
              <img class="detail-img" :src="item.url">
              <img class="detail-img-hot" v-if="item.hot!=''" :src="item.hot">
              <div class="detail-desc">
                <p class="detail-content">{{item.content}}</p>
              </div>
            </div>
          </div>
        </swiper-slide>
        <div class="swiper-scrollbar"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      swiperOption: {
        scrollbar: '.swiper-scrollbar'
      },
      detailList: [{
        id: '001',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_250x250_57ac4faa.jpg',
        content: '上海迪士尼',
        hot: 'http://img1.qunarzz.com/piao/fusion/1710/ab/159673b63e6ca702.png'
      }, {
        id: '002',
        url: 'http://img1.qunarzz.com/tuan/team2/1507/2c/83e0e0e7ae082a.jpg_250x250_87692c41.jpg',
        content: '上海陆家嘴嘴',
        hot: 'http://img1.qunarzz.com/piao/fusion/1710/2d/36d0c4adaebbbc02.png'
      }, {
        id: '003',
        url: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_250x250_963fe222.jpg',
        content: '上海欢乐谷',
        hot: 'http://img1.qunarzz.com/piao/fusion/1710/67/edc47ffef9e96b02.png'
      }, {
        id: '004',
        url: 'http://img1.qunarzz.com/sight/p0/1904/d5/d579b03a110d75a8a3.img.jpg_250x250_cf952d13.jpg',
        content: '上海动物园',
        hot: ''
      }, {
        id: '005',
        url: 'http://img1.qunarzz.com/sight/p0/1707/62/62981f052681ef5ba3.img.jpg_250x250_11d6ec49.jpg',
        content: '上海夜总会',
        hot: ''
      }]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.detailList.forEach((item, index) => {
        const page = Math.floor(index / 4)
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
  .recommend
    width 100%
    .title
      width 100%
      height 4rem
      .title-group
        width 100%
        height 2rem
        margin-top 1rem
        float left
        padding-left 1rem
        font-family 微软雅黑
        .title-img
          width 1rem
          height 1rem
          margin-top .5rem
        .title-all
          float right
          font-size .4rem
          line-height 1rem
          margin-top 1rem
    .detail
      width 100%
      height 7.5rem
      .detail-group
        width 21.2%
        height 7.5rem
        float left
        margin-left 3%
        position relative
        .detail-img
          height 6rem
        .detail-img-hot
          height 1.3rem
          width 50%
          position absolute
          top 0
          left 0
        .detail-desc
          font-size .8rem
          line-height 1.3rem
          text-align center
</style>
