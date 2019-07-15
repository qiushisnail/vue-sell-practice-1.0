<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li class="menu-item" v-for="good in goods" :class="{'current':currentIndex === $index}">
          <span class="text border-1px">
            <span class="icon" v-if="good.type > 0"></span>{{good.name}}
          </span>
        </li>
      </ul>
    </div>
    <div class="foods-wrapper"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  const ERR_OK = 0
  export default {
    data() {
      return {
        goods: {},
        currentIndex: 1
      }
    },
    created() {
      this.$http.get('/api/goods').then((res, req) => {
        res = res.body
        if (res.errno === ERR_OK) {
          this.goods = res.data
          console.log(this.goods)
        }
      })
    }
  }
</script>

<style lang="stylus" rel='stylesheet/stylus'>
  @import "../../common/stylus/mixin.styl"

  .goods
    display: flex
    position: absolute
    top: 174px
    bottom: 46px
    width: 100%
    overflow: hidden

    & > .menu-wrapper
      flex: 0 0 80px
      width: 80px
      background: #f3f5f7

      .menu-item
        display: table
        width: 56px
        height: 54px
        padding: 0 12px
        line-height: 14px
        font-size: 12px


        & > .text
          display: table-cell
          vertical-align: middle
          font-weight: 200
          border-1px(rgba(7, 17, 27, 0.1))
        &.current
          background: rgb(255, 255, 255)

          .text
            font-weight: bold
            border-none()
    & > .foods-wrapper
      flex: 1

</style>
