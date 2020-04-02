<template>
    <div class="container" @click="handleGallaryClick">
      <div class="wrapper">
        <swiper :options="swiperOptions">
          <swiper-slide v-for="(item, index) of imgs" :key="index">
            <img class="gallary-img" :src="item">
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  }
}
</script>

<style scoped lang="stylus">
  .container >>> .swiper-container
    overflow inherit
  .container
    position fixed
    top: 0
    left: 0
    right: 0
    bottom: 0
    background: #000
    display flex
    flex-direction column
    justify-content center
    z-index 99
    .wrapper
      width: 100%
      padding-bottom: 100%
      height: 0
      .gallary-img
        width: 100%
      .swiper-pagination
        color white
        bottom: -1rem
</style>
