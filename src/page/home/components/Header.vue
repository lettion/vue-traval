<template>
    <div class="header">
      <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/景点/游玩/主题
      </div>
      <router-link to="/city">
        <div class="header-right">
          {{this.city}}
          <span class="iconfont arrow-icon">&#xe64a;</span>
        </div>
      </router-link>
    </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'Header',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style scoped lang="stylus">
  @import "~styles/varibles.styl"
  .header
    display :flex
    line-height .86rem
    background: $bgColor
    color: #ffffff
    .header-left
      float:left
      width:.64rem
      text-align: center
      .back-icon
        font-size:.4rem
    .header-input
      padding-left: .2rem
      flex:1
      line-height:.64rem
      border-radius .1rem
      background: #fff
      height:.64rem
      margin-top:.12rem
      margin-left:.2rem
      color: #ccc
    .header-right
      float :right
      min-width :1.04rem
      padding: 0 .1rem
      text-align: center
      color white
      .arrow-icon
        font-size .20rem
</style>
