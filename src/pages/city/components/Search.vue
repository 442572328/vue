<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <div v-show="keyword" class="search-content" ref="search">
      <ul>
        <li class="search-item" v-for="item in list" :key="item.id"  @click="handleCityClick(item.name)">{{item.name}}</li>
        <li v-show="hasNoData" class="search-item">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        if (this.keyword === '' || !this.keyword) {
          this.list = []
          return
        }
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new BScroll('.search-content')
  }
}
</script>

<style lang="stylus" scoped>
  @import "../../../../src/assets/style/variables.styl"
  .search
    height 2.2rem
    background-color $bgColor
    padding 0 .4rem
    .search-input
      box-sizing border-box
      height 1.8rem
      width 100%
      text-align center
      border-radius .25rem
      padding 0 .3rem
  .search-content
    position absolute
    top 5.2rem
    bottom 0
    left 0
    right 0
    background-color $blankColor
    overflow hidden
    z-index 1
    .search-item
      line-height 1.5rem
      padding-left 1rem
      color #666
      margin .5rem 0
      font-size .95rem
      overflow hidden
</style>
