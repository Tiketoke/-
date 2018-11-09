<template>
    <div class="header">
      <div class="content-wrapper">
        <div class="avatar">
          <img width="64" height="64" :src="seller.avatar">
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        name: "Home",
        props:{         //父子传值
          seller:Object
        }
    }
</script>

<style lang="stylus">
  @import "../../common/stylus/mixin"
  .header
    position: relative
    overflow: hidden
    color: #fff
    background: rgba(7, 17, 27, 0.5)
    .content-wrapper
      position: relative
      padding: 24px 12px 18px 24px
      font-size: 0
      .avatar
        display: inline-block
        vertical-align: top
        img
          border-radius: 2px


</style>
