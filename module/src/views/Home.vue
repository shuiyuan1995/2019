<style lang="stylus" scoped>
.home
  height 100%
  min-height 100vh
  background #000
  padding-top 1px;
</style>

<template>
  <div class="home">
    <ParticleClock></ParticleClock>
  </div>
</template>

<script>
// @ is an alias to /src
import ParticleClock from '@/components/ParticleClock.vue'

export default {
  components: {
    ParticleClock
  }
}
</script>
