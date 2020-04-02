<template>
    <div class="list" ref="wrapper">
     <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
          <div class="button-list">
            <div class="button-wrapper">
            <div class="button">
              {{this.currentCity}}
            </div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper"
               v-for="item of hot"
               :key="item.id"
               @click="handleClick(item.name)">
            <div class="button">
              {{item.name}}
            </div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(items,key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
          <div class="item-list" v-for="item of items" :key="item.id" @click="handleClick(item.name)">
            <div class="item border-bottom">{{item.name}}</div>
          </div>
      </div>
     </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'List',
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true
    })
  },
  watch: {
    letter () {
      if (this.letter) {
        const el = this.$refs[this.letter][0]
        this.scroll.scrollToElement(el)
      }
    }
  }
}
</script>

<style scoped lang="stylus">
  .list
    position absolute
    left: 0
    top: 1.58rem
    right: 0
    bottom: 0
    overflow: hidden
    .border-topbottom
      &:before
        border-color: #ccc
      &:after
        border-color: #ccc
    .border-bottom
      &:before
        border-color: #ccc
    .title
      line-height: .54rem
      padding-left: .2rem
      background: #eee
      color #666
      font-size .26rem
    .button-list
      padding:.1rem .6rem .1rem .1rem
      overflow hidden
      .button-wrapper
        width: 33.3%
        float: left
        .button
          margin: .1rem
          text-align: center
          border .02rem solid #ccc
          padding: .1rem
          border-radius .06rem
    .item-list
      .item
        line-height: .76rem
        padding-left: .2rem
</style>
