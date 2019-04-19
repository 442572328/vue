<template>
    <div class="content">
      <div v-for="(item,index) in list" :key="index" class="title">
        <span class="iconfont title-icon">&#xe63f;</span>
        {{item.title}}
        <div v-show="item.children">
          <detail-content :list="item.children"></detail-content>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'DetailContent',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../../assets/style/variables.styl'
  .content
    background-color $blankColor
    .title
      line-height 1.5rem
      margin .8rem .8rem
</style>
