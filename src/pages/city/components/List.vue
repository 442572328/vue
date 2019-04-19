<template>
    <div class="list" ref="wrapper">
      <div class="content">
        <div class="current-city">
          <div class="current-title">当前城市</div>
          <div class="current-wrapper">
            <div class="current-cont">{{$store.state.city}}</div>
          </div>
        </div>
        <div class="hot-city">
          <div class="hot-title">热门城市</div>
          <div class="hot-wrapper">
            <div class="hot-cont" v-for="item in hotCities" :key="item.id" @click="handleCityClick(item.name)" >{{item.name}}</div>
          </div>
        </div>
        <div class="list-city" v-for="(item,key) in cities" :key="key"  :ref="key">
          <div class="list-title">{{key}}</div>
          <div class="list-cont" v-for="innerItem in item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .list
    position absolute
    top 5.3rem
    right 0
    bottom 0
    left 0
    padding .1rem
    overflow hidden
    .current-city
      font-size .95rem
      .current-title
        line-height 1.5rem
        padding-left 1rem
        background-color #eee
      .current-wrapper
        .current-cont
          width 25%
          display inline-block
          margin .8rem
          padding .1rem 0
          border 1px #ccc solid
          border-radius .2rem
          text-align center
    .hot-city
      font-size .95rem
      .hot-title
        padding-left 1rem
        background-color #eee
        line-height 1.5rem
      .hot-wrapper
        .hot-cont
          width 25%
          display inline-block
          margin .8rem
          padding .1rem 0
          border 1px #ccc solid
          border-radius .2rem
          text-align center
    .list-city
      font-size .95rem
      .list-title
        padding-left 1rem
        background-color #eee
        line-height 1.5rem
      .list-cont
        padding-left 1rem
        margin .5rem 0
</style>
