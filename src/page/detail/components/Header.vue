<template>
    <div>
      <router-link tag="div" to="/" class="header-abs" v-show="showHeader">
        <div class="iconfont header-abs-back">&#xe624;</div>
      </router-link>
      <div class="header-fix" v-show="!showHeader" :style="opacityHeader">
        景点选择
        <router-link to="/">
          <span class="iconfont header-fix-back">&#xe624;</span>
        </router-link>
      </div>
    </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showHeader: true,
      opacityHeader: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityHeader = { opacity }
        this.showHeader = false
      } else {
        this.showHeader = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  unmounted () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .header-abs
    position absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    border-radius .4rem
    background: rgba(0, 0, 0, .8)
    line-height:.8rem
    text-align: center
    .header-abs-back
      font-size .4rem
      color #ffffff
  .header-fix
    height:$headerHeight
    line-height: $headerHeight
    background: $bgColor
    text-align: center
    color white
    font-size .32rem
    position fixed
    top: 0
    right: 0
    left: 0
    z-index 999
    .header-fix-back
      position absolute
      top: 0
      left: 0
      width: .64rem
      text-align: center
      font-size: .4rem
      color white
</style>
