<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item" v-for="item of list" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>

<style scoped lang="stylus">
  @import "~styles/mixins.styl"
  .recommend-title
    line-height:.8rem
    text-indent .2rem
    background: #eee
  .item-img-wrapper
    overflow hidden
    padding-bottom:37.09%
    height: 0
    width: 100%
    .item-img
      width: 100%
  .item-info
    padding: .1rem
    .item-title
      line-height:.54rem
      font-size .32rem
    .item-desc
      line-height: .4rem
      color #ccc
      ellipsis()
</style>
