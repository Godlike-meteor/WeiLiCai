<!-- Detail-Header -->
<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      文章详情
      <router-link to='/'>
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        var opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
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
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width .6rem
    height .6rem
    line-height .6rem
    text-align center
    border-radius .4rem
    background rgba(0,0,0,.4)
    .header-back
      color #ffffff
      font-size .32rem
  .header-fixed
    position fixed
    top 0
    left 0
    right 0
    height .86rem
    line-height .86rem
    text-align center
    font-size .32rem
    font-weight bold
    background #fff
    .header-fixed-back
      position absolute
      top 0
      left 0
      width .64rem
      text-align center
      font-size .4rem
      color #000
</style>
