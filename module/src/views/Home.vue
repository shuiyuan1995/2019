<style lang="stylus" scoped>
.home
  height 100%
  min-height 100vh
  background #000
  padding-top 1px;
</style>

<template>
  <div class="home">
    <blackhole></blackhole>
  </div>
</template>

<script>
// @ is an alias to /src
import blackhole from '@/components/blackhole.vue'

export default {
  components: {
    blackhole
  }
}
</script>
