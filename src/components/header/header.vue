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
      <div class="supports-count" v-if="seller.supports" @click="showDetail">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper" @click="showDetail">
      <span class="icon"></span><span class="bulletin">{{seller.bulletin}}</span>
      <i class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img width="100%" height="100%" :src="seller.avatar" alt="背景图">
    </div>
    <div class="detail" v-show="showDetailInfo" transition="fade">
      <div class="detail-wrapper clearfix">
        <div class="detail-main">
          <h1 class="name">{{seller.name}}</h1>
          <div class="star-wrapper">
            <star :size="48" :score="seller.score"></star>
          </div>
          <div class="title-wrapper">
            <line text="优惠信息"></line>
          </div>
          <ul class="bulletin" v-if="seller.supports">
            <li class="support-item" v-for="support in seller.supports" track-by="$index">
              <span class="icon" :class="classMap[support.type]"></span>
              <span class="description">{{support.description}}</span>
            </li>
          </ul>
          <div class="title-wrapper">
            <line text="商家公告"></line>
          </div>
          <div class="bulletin-info">
            <p>{{seller.bulletin}}</p>
          </div>
        </div>
      </div>
      <div class="detail-close">
        <i class="icon-close" @click="closeDetail"></i>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import star from 'components/star/star'
  import line from 'components/line/line'

  export default {
    data() {
      return {
        showDetailInfo: false
      }
    },
    props: {
      seller: {
        type: Object
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
    },
    methods: {
      showDetail() {
        this.showDetailInfo = true
      },
      closeDetail() {
        this.showDetailInfo = false
      }
    },
    components: {
      star,
      line
    }
  }
</script>

<style lang="stylus" rel='stylesheet/stylus'>
  @import '../../common/stylus/mixin.styl'

  .header
    position: relative
    color: #ffffff
    background: rgba(7, 17, 27, 0.5)
    overflow: hidden

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
        text-align: center

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
      width: 100%
      height: 100%
      z-index: -1
      filter: blur(10px)

    & > .detail
      position: fixed
      top: 0
      left: 0
      z-index: 100
      width: 100%
      height: 100%
      overflow: auto
      text-align: center
      transition: all 0.5s
      backdrop-filter: blur(10px)

      &.fade-transition
        opacity: 1
        background: rgba(7, 17, 27, 0.8)

      &.fade-enter, &.fade-leave
        opacity: 0
        background: rgba(7, 17, 27, 0)

      & > .detail-wrapper
        width: 100%
        min-height: 100%

        & > .detail-main
          margin-top: 64px
          padding-bottom: 64px

          & > .name
            line-height: 16px
            font-size: 16px
            font-weight: bold

          & > .star-wrapper
            margin-top: 16px
            padding: 2px 0

          & > .title-wrapper
            margin: 28px auto 24px auto
            width: 80%

          & > .bulletin
            width: 80%
            margin: 0 auto
            text-align: left

            & > .support-item
              font-size: 0
              padding: 0 12px
              margin-bottom: 12px

              &:last-child
                margin-bottom: 0

              & > .icon
                display: inline-block
                vertical-align: top
                margin-right: 6px
                width: 16px
                height: 16px
                background-size: 16px 16px
                background-repeat: no-repeat

                &.discount
                  bg-image("discount_2")

                &.decrease
                  bg-image("decrease_2")

                &.guarantee
                  bg-image("guarantee_2")

                &.invoice
                  bg-image("invoice_2")

                &.special
                  bg-image("special_2")

              & > .description
                line-height: 16px
                font-size: 12px
                font-weight: 200

          & > .bulletin-info
            width: 80%
            margin: 0 auto

            & > p
              padding: 0 12px
              line-height: 24px
              font-size: 12px
              font-weight: 200
              text-align: left

      & > .detail-close
        position: relative
        width: 32px
        height: 32px
        margin: -64px auto 0 auto
        clear: both

        & > .icon-close
          font-size: 32px
          color: rgba(255, 255, 255, 0.8)

</style>
