<style lang="stylus" scoped>
.home
  height 100%
  min-height 100vh
  background #000
  padding-top 1px;
</style>

<template>
  <div class="home">
    <swiper></swiper>
  </div>
</template>

<script>
// @ is an alias to /src
import swiper from '@/components/swiper.vue'

export default {
  components: {
    swiper
  }
}
</script>
