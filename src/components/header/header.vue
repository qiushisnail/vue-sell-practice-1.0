<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img width=64 height=64 :src="seller.avatar" alt="商标">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">
            {{seller.name}}
          </span>
        </div>
        <div class="description">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <div class="supports" v-if="seller.supports">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="description">
            {{seller.supports[0].description}}
          </span>
        </div>
      </div>
      <div class="supports-count" v-if="seller.supports">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper">
      <span class="icon"></span><span class="bulletin">{{seller.bulletin}}</span>
      <i class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img width="100%" height="100%" :src="seller.avatar" alt="背景图">
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
    }
  }
</script>

<style lang="stylus" rel='stylesheet/stylus'>
  @import '../../common/stylus/mixin.styl'

  .header
    position: relative
    color: #ffffff
    background: rgba(7, 17, 27, 0.5)

    & > .content-wrapper
      position: relative
      padding: 24px 12px 18px 24px
      font-size: 0

      & > .avatar
        display: inline-block
        vertical-align: top

        & > img
          border-radius: 2px

      & > .content
        display: inline-block
        margin-left: 16px

        & > .title
          margin: 2px 0 8px

          & > .brand
            display: inline-block
            vertical-align: top
            margin-right: 6px
            width: 30px
            height: 18px
            bg-image("brand")
            background-position: center center
            background-repeat: no-repeat
            background-size: cover

          & > .name
            line-height: 18px
            font-size: 16px
            font-weight: bold

        & > .description
          margin-bottom: 10px
          font-size: 12px

        & > .supports
          & > .icon
            display: inline-block
            vertical-align: top
            margin-right: 4px
            width: 12px
            height: 12px
            background-size: 12px 12px
            background-repeat: no-repeat

            &.discount
              bg-image("discount_1")

            &.decrease
              bg-image("decrease_1")

            &.guarantee
              bg-image("guarantee_1")

            &.invoice
              bg-image("invoice_1")

            &.special
              bg-image("special_1")

          & > .description
            line-height: 12px
            font-size: 10px

      & > .supports-count
        position: absolute
        right: 12px
        bottom: 14px
        line-height: 24px
        padding: 0 8px
        height: 24px
        background: rgba(0, 0, 0, 0.2)
        border-radius: 14px

        & > .count
          vertical-align: top
          margin-right: 2px
          font-size: 10px

        & > .icon-keyboard_arrow_right
          vertical-align: top
          line-height: 24px
          font-size: 10px

    & > .bulletin-wrapper
      position: relative
      line-height: 28px
      height: 28px
      padding: 0 22px 0 12px
      white-space: nowrap
      overflow: hidden
      text-overflow: ellipsis
      background: rgba(7, 17, 27, 0.2)

      & > .icon
        display: inline-block
        vertical-align: top
        margin-top: 8px
        width: 22px
        height: 12px
        bg-image("bulletin")
        background-size: 22px 12px
        background-repeat: no-repeat

      & > .bulletin
        margin: 0 4px
        vertical-align: top
        font-size: 10px

      & > .icon-keyboard_arrow_right
        position: absolute
        font-size: 10px
        right: 12px
        top: 8px

    & > .background
      position: absolute
      top: 0
      left: 0
      z-index: -1
      width: 100%
      height: 100%
      filter: blur(10px)
</style>
