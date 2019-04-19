<template>
  <div class="header">
    <router-link to="/">
      <span class="iconfont back-icon">&#xe624;</span>
    </router-link>
    <span>城市列表</span>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .header
    width 100%
    height 3rem
    line-height 3rem
    background-color $bgColor
    text-align center
    color $backColor
    .back-icon
      position absolute
      top 0
      left 0
      text-align center
      width 2rem
</style>
