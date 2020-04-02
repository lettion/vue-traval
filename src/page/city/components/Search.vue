<template>
  <div>
    <div class="search">
      <input v-model="keyword" type="text" placeholder="输入城市名或拼音" class="search-input">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li v-for="item of list" :key="item.id"
            class="search-item border-bottom"
            @click="handleClick(item.name)">
          {{item.name}}
        </li>
        <li class="search-item border-bottom" v-show="hasNotData">没有匹配到数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import {mapMutations} from 'vuex'
import BScroll from 'better-scroll'
export default {
  name: 'Search',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  computed: {
    hasNotData () {
      return !this.list.length
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search, {
      click: true
    })
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  methods: {
    handleClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .search
    height: .72rem
    background: $bgColor
    padding:0 .1rem
    box-sizing border-box
    .search-input
      height: .62rem
      line-height: .6rem
      padding .1rem
      box-sizing border-box
      border-radius .1rem
      width: 100%
      text-align: center
      color: #666
  .search-content
    position absolute
    left: 0
    right: 0
    bottom: 0
    top: 1.58rem
    z-index 99
    background: #ccc
    overflow: hidden
    .search-item
      line-height: .62rem
      padding-left: .2rem
      background: #fff
      color: #666
</style>
