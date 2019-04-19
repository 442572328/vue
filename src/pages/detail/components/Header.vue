<template>
  <div class="header">
    <router-link to="/">
      <div v-show="showAbs" class="header-abs"><strong><span class="iconfont back-icon">&#xe624;</span></strong></div>
    </router-link>
    <div v-show="!showAbs" class="header-fixed" :style="opacityStyle">
      <router-link to="/">
        <span class="iconfont fixed-back-icon">&#xe624;</span>
      </router-link>
      <span>{{sightName}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  props: {
    sightName: String
  },
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 1
      }
    }
  },
  methods: {
    handleScroll () {
      let timer = null
      if (timer) {
        clearTimeout(timer)
      }
      setTimeout(() => {
        const top = document.documentElement.scrollTop
        if (top >= 40) {
          let opacity = top / 200
          opacity = opacity > 1 ? 1 : top / 200
          this.opacityStyle = {
            opacity: opacity
          }
          this.showAbs = false
        } else {
          this.showAbs = true
        }
      }, 40)
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../../assets/style/variables.styl'
  .header
    width 100%
    .header-abs
      position absolute
      top .5rem
      left .5rem
      background-color rgba(0,0,0,0.8)
      height 2rem
      width 2rem
      border-radius 1rem
      line-height 2rem
      text-align center
      .back-icon
        color $backColor
        font-size 1.2rem
    .header-fixed
      position fixed
      top 0
      left 0
      width 100%
      height 3rem
      line-height 3rem
      background-color $bgColor
      color $backColor
      text-align center
      .fixed-back-icon
        position absolute
        left .7rem
        font-size 1.2rem
</style>
