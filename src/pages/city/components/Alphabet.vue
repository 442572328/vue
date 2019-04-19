<template>
    <div class="alphabet">
      <ul class="list">
        <li @touchstart="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd" @click="letterChange" v-for="item in letters" :key="item" class="item" :ref="item">{{item}}</li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    letterChange (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer != null) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const startY = this.startY
          const touchY = e.touches[0].clientY - 82 - 31
          const index = Math.floor((touchY - startY) / 24)
          this.$emit('change', this.letters[index])
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .alphabet
    .list
      width 1rem
      position absolute
      top 6.4rem
      right 0
      bottom 0
      display flex
      flex-direction column
      justify-content center
      .item
        text-align center
        line-height 1.5rem
        color $bgColor
        font-size .95rem
</style>
