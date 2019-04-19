<template>
  <div class="favorate">
    <div class="title">
      <img class="fav-img" src="http://img1.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png">
      <span class="fav-content">猜你喜欢</span>
    </div>
    <div class="container" v-for="(page,index) in pages" :key="index">
      <router-link v-for="item in page" :key="item.id" :to="/detail/+item.id">
        <div class="detail">
            <div class="detail-img">
              <img :src="item.url">
            </div>
            <div class="detail-content">
              <div class="detail-content-title">
                {{item.title}}
              </div>
              <div class="detail-content-like">
                <span class="iconfont star-icon">&#xe761;</span><span class="iconfont star-icon">&#xe761;</span><span class="iconfont star-icon">&#xe761;</span><span class="iconfont star-icon">&#xe761;</span><span class="iconfont star-icon">&#xe761;</span>
                <span class="iconfont star-icon-desc">{{item.num}}条评论</span>
              </div>
              <div class="detail-content-price">
                <span class="iconfont yuan-icon">&#xe63c;</span><span class="price">{{item.price}}</span><span class="price-desc">起</span>
                <span class="district">{{item.district}}</span>
              </div>
              <div class="detail-content-desc">
                {{item.desc}}
              </div>
            </div>
        </div>
      </router-link>
    </div>
    <div class="more">
      <span :class="{active:isActive}" @click="nextPage" disable="disable">查看更多产品</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeFavorate',
  data () {
    return {
      favList: [{
        id: '001',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
        title: '上海迪士尼乐园',
        num: '2250',
        price: '225',
        district: '普陀区',
        desc: '全球最大的迪士尼城堡'
      }, {
        id: '002',
        url: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_200x200_9a7794fc.jpg',
        title: '上海欢乐谷',
        num: '2800',
        price: '280',
        district: '奉贤区',
        desc: '好玩的很'
      }, {
        id: '003',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
        title: '上海迪士尼乐园',
        num: '2250',
        price: '225',
        district: '普陀区',
        desc: '全球最大的迪士尼城堡'
      }, {
        id: '004',
        url: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_200x200_9a7794fc.jpg',
        title: '上海欢乐谷',
        num: '2800',
        price: '280',
        district: '奉贤区',
        desc: '好玩的很'
      }, {
        id: '005',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
        title: '上海迪士尼乐园',
        num: '2250',
        price: '225',
        district: '普陀区',
        desc: '全球最大的迪士尼城堡'
      }, {
        id: '006',
        url: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_200x200_9a7794fc.jpg',
        title: '上海欢乐谷',
        num: '2800',
        price: '280',
        district: '奉贤区',
        desc: '好玩的很'
      }, {
        id: '007',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
        title: '上海迪士尼乐园',
        num: '2250',
        price: '225',
        district: '普陀区',
        desc: '全球最大的迪士尼城堡'
      }, {
        id: '008',
        url: 'http://img1.qunarzz.com/sight/p0/1811/e4/e4b9b471d2afc473a3.img.jpg_200x200_9a7794fc.jpg',
        title: '上海欢乐谷',
        num: '2800',
        price: '280',
        district: '奉贤区',
        desc: '好玩的很'
      }, {
        id: '009',
        url: 'http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg',
        title: '上海迪士尼乐园',
        num: '2250',
        price: '225',
        district: '普陀区',
        desc: '全球最大的迪士尼城堡'
      }],
      current: 1,
      disable: false,
      isActive: false
    }
  },
  computed: {
    pages () {
      const pages = []
      const page = this.current
      this.favList.forEach((item, index) => {
        // const page = Math.floor(index / 6)
        if (!pages[page]) {
          pages[page] = []
        }
        // pages[page].push(item)
        if (index < page * 4) {
          if (index === page * 4 - 1) {
            item.desc = ''
          }
          pages[page].push(item)
        }
      })
      return pages
    }
  },
  methods: {
    nextPage () {
      this.current++
      if (this.pages[this.current].length === this.favList.length) {
        this.disable = false
        this.isActive = true
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .favorate
    width 100%
    .title
      width 100%
      height 3rem
      padding-left 1rem
      padding-top 1rem
    .fav-img
      width 1rem
      height 1rem
    .fav-content
      font-family "微软雅黑"
    .detail
      width 100%
      height 9rem
      margin-top 1rem
      position relative
      padding-bottom 40%
      overflow hidden
      .detail-img
        width 25%
        height 7rem
        position absolute
        top 0
        left 1rem
      .detail-content
        width 70%
        height 9rem
        float right
        .detail-content-title
          width 100%
          height 1rem
          font-family "微软雅黑"
          margin-top 1rem
          color $darkTextColor
        .detail-content-like
          margin-top .5rem
          .star-icon
            color orange
          .star-icon-desc
            font-size .7rem
            color $smFontColor
            padding-left 1rem
        .detail-content-price
          position relative
          .yuan-icon
            color orange
            font-size .1rem
          .price
            font-size 1.2rem
            color orange
          .price-desc
            font-size .7rem
            color $smFontColor
          .district
            font-size .7rem
            color #6C6C6C
            position absolute
            right 1rem
            top .4rem
        .detail-content-desc
          float left
          margin-top 3rem
          font-size .7rem
          color red
    .more
      text-align center
      color #00AFC7
      font-size .8rem
      .active
        color: gray
</style>
