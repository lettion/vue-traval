<template>
    <div class="header">城市选择
      <router-link to="/">
        <span class="iconfont back-icon">&#xe624;</span>
      </router-link>
    </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .header
    height:$headerHeight
    line-height: $headerHeight
    background: $bgColor
    text-align: center
    color white
    font-size .32rem
    overflow hidden
    position relative
    .back-icon
      position absolute
      top: 0
      left: 0
      width: .64rem
      text-align: center
      font-size: .4rem
      color white
</style>
