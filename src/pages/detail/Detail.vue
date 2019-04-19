<template>
    <div>
      <detail-banner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"></detail-banner>
      <detail-header :sightName="sightName"></detail-header>
      <detail-content :list="list"></detail-content>
    </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailContent from './components/Content'
import axios from 'axios'
export default {
  name: 'Detail',
  components: {DetailContent, DetailHeader, DetailBanner},
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: []
    }
  },
  methods: {
    getDetail () {
      axios.get('/static/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.handleGetDetailSuccess)
    },
    handleGetDetailSuccess (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetail()
  }
}
</script>

<style lang="stylus" scoped>
</style>
