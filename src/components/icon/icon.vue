<template>
  <span :class="[iconType,classMap[supporttype]]"></span>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      category: {
        type: Number
      },
      supporttype: {
        type: Number
      }
    },
    computed: {
      iconType() {
        return 'icon-' + this.category
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
    }
  }
</script>

<style lang="stylus" rel='stylesheet/stylus'>
  @import '../../common/stylus/mixin.styl'
  .icon-1
    display: inline-block
    vertical-align: top
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

  .icon-2
    display: inline-block
    vertical-align: top
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

  .icon-3
    display: inline-block
    vertical-align: top
    width: 12px
    height: 12px
    background-size: 12px 12px
    background-repeat: no-repeat

    &.discount
      bg-image("discount_3")

    &.decrease
      bg-image("decrease_3")

    &.guarantee
      bg-image("guarantee_3")

    &.invoice
      bg-image("invoice_3")

    &.special
      bg-image("special_3")

  .icon-4
    display: inline-block
    vertical-align: top
    width: 16px
    height: 16px
    background-size: 16px 16px
    background-repeat: no-repeat

    &.discount
      bg-image("discount_4")

    &.decrease
      bg-image("decrease_4")

    &.guarantee
      bg-image("guarantee_4")

    &.invoice
      bg-image("invoice_4")

    &.special
      bg-image("special_4")
</style>
