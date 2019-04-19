<template>
    <div class="header">
      <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input" type="text">
        <span class="iconfont search-icon">&#xe638;</span>
        请输入景点/城市/游玩主题
      </div>
      <router-link to="/city">
        <div class="header-right">
          {{$store.state.city}}<span class="iconfont arrow-icon">&#xe64a;</span>
        </div>
      </router-link>
    </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
  @import '../../../assets/style/variables.styl'
  .header
      display flex
      line-height 3.0rem
      background-color $bgColor
      color #fff
    .header-left
      width 2.0rem
      float left
      .back-icon
        margin-left .6rem
  .header-input
      flex 1
      height 2.0rem
      line-height 2.0rem
      margin-top .5rem
      margin-left .4rem
      padding-left .4rem
      background #fff
      border-radius .3rem
      color: #ccc
      text-align left
    .search-icon
        font-size:1.2rem
  .header-right
      margin-left .3rem
      margin-right .3rem
      float right
      text-align center
      color $backColor
</style>
