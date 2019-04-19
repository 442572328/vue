<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <home-recommend></home-recommend>
    <home-favorate></home-favorate>
    <home-weekend></home-weekend>
    <home-footer></home-footer>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeFavorate from './components/Favorate'
import HomeWeekend from './components/Weekend'
import HomeFooter from './components/Footer'
export default {
  name: 'Home',
  components: {
    HomeFooter,
    HomeWeekend,
    HomeFavorate,
    HomeRecommend,
    HomeIcons,
    HomeSwiper,
    HomeHeader
  }
}
</script>

<style scoped>

</style>
