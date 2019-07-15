<template>
  <div class="line-wrapper">
    <div class="line"></div>
    <div class="text">{{text}}</div>
    <div class="line"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      text: {
        type: String
      }
    }
  }
</script>

<style lang="stylus" rel='stylesheet/stylus'>
  .line-wrapper
    display: flex
    width: 100%
    & > .text
      line-height: 14px
      font-size: 14px
      font-weight: bold
      padding: 0 12px

    & > .line
      position: relative
      flex: 1
      border-bottom: 1px solid rgba(255,255,255,0.2)
      top: -6px

</style>
