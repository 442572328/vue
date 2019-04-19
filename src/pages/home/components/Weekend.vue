<template>
    <div class="weekend">
      <div class="title">周末去哪儿</div>
      <div v-for="item in prodList" :key="item.id" class="weekend-box">
        <div class="img">
          <img class="img-url" :src="item.url">
        </div>
        <div class="prod">
          <div class="prod-box">
            <div class="prod-name">{{item.name}}</div>
            <div class="prod-desc">{{item.desc}}</div>
          </div>
        </div>
      </div>
      <div class="warn">
        <span class="iconfont warn-img">&#xe810;</span><span class="warn-cont"><b>票面价</b></span><span>是指通过景区指定窗口售卖的纸质门票上标注的价格</span>
      </div>
    </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data () {
    return {
      prodList: [{
        id: '001',
        url: 'http://img1.qunarzz.com/sight/source/1505/7d/df6ff468331c43.jpg_r_640x214_1f3783d0.jpg',
        name: '上海必打卡',
        desc: '中西合璧，现代和传统各有各的精彩'
      }, {
        id: '002',
        url: 'http://img1.qunarzz.com/sight/source/1603/cf/762cb38938a093.jpg_r_640x214_e02c18ef.jpg',
        name: '上海看花',
        desc: '一起去看花吧'
      }, {
        id: '003',
        url: 'http://img1.qunarzz.com/sight/source/1603/ad/69b0fc5f48ad5f.jpg_r_640x214_b0fd5c7b.jpg',
        name: '周末亲子爱玩',
        desc: '游乐场的惊险刺激,带上儿子一起领略...'
      }, {
        id: '004',
        url: 'http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg',
        name: '上海城市观光',
        desc: '上海的夜景一览无余,美不胜收啊...'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .weekend
    width 100%
    .title
      margin-top 1rem
      height 2rem
      line-height 2rem
      background-color #eaeaea
      font-size .95rem
      padding-left .8rem
    .weekend-box
      width 100%
      .img
        width 100%
        .img-url
          width 100%
    .prod
      width 100%
      height 4.5rem
      .prod-box
        margin-top .5rem
        margin-bottom .5rem
        height 4rem
        width 100%
        .prod-name
          padding-top .85rem
          font-size .95rem
          padding-left .8rem
        .prod-desc
          font-size .8rem
          padding-left .8rem
          color $smFontColor
    .warn
      font-size .7rem
      color $smFontColor
      padding-left .8rem
      .warn-img
        font-size .65rem
      .warn-cont
        margin-left .2rem
</style>
