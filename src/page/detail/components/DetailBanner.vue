<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="info-title">
          {{this.sightName}}
        </div>
        <div class="info-number">
          <span class="info-icon iconfont">&#xe63e;</span>12</div>
      </div>
    </div>
    <fade-animation>
      <common-gallary :imgs="this.gallaryImgs" v-show="showGallary" @close="handleGallaryClick"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/animation/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClick () {
      this.showGallary = false
    }
  }
}
</script>

<style scoped lang="stylus">
  .banner
    padding-bottom: 55%
    overflow: hidden
    height: 0
    position relative
    .banner-image
      width: 100%
    .banner-info
      position absolute
      bottom: 0
      left: 0
      right: 0
      line-height: .6rem
      display flex
      color #fff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
      .info-title
        flex 1
        font-size: .32rem
        padding: 0 .2rem
      .info-number
        margin-top: .14rem
        height .32rem
        line-height: .32rem
        padding: 0 .4rem
        border-radius .4rem
        background: rgba(0, 0, 0, .8)
        font-size .24rem
        .info-icon
          font-size .24rem
</style>
