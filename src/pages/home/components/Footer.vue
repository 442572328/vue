<template>
    <div class="footer">
      <div class="icons">
          <span class="iconfont air-img">&#xe70e;</span><span class="air-cont"><u>机票</u></span>
          <span class="iconfont hotel">&#xe979;</span><span class="hotel-cont"><u>酒店</u></span>
          <span class="iconfont room">&#xe662;</span><span class="room-cont"><u>公寓</u></span>
          <span class="sep">|</span>
          <span class="iconfont more">&#xe63f;</span><span class="more-cont"><u>更多</u></span>
      </div>
      <div class="desc">
        ©Copyright 2019 老汉旅游
      </div>
      <div class="free">免责声明:本项目仅作为演示和测试用,无任何商业用途</div>
    </div>
</template>

<script>
export default {
  name: 'HomeFooter'
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
    .footer
      margin-top 1rem
      padding-top 1.5rem
      width 100%
      color $smFontColor
      background-color $blankColor
      .icons
        font-size .7rem
        text-align center
        .iconfont
          font-size 1.2rem
          margin-left 1rem
        .sep
          margin-left 1.5rem
          margin-right .5rem
      .desc
        border-top 1px solid $smFontColor
        margin-top 1.15rem
        font-size .9rem
        color $smFontColor
        text-align center
        background-color $blankColor
        padding-top 1rem
        margin-bottom .2rem
      .free
        margin-top 1.15rem
        font-size .9rem
        color $smFontColor
        text-align center
        background-color $blankColor
        padding-top 1rem
        margin-bottom .2rem
</style>
