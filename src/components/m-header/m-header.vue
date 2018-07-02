<template>
<div class="myheader">
  <div class="logo"></div>
  <h1 class="title">maomao music</h1>
  <router-link to="/user" class="mime">
    <i class="fa fa-user-o myicon" aria-hidden="true"></i>
  </router-link>
</div>
</template>

<script type="text/ecmascript-6">

</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import "../../common/stylus/mixin.styl"
  @import "../../common/stylus/variable"
.myheader
  position: relative
  height: 44px
  text-align: center
  color: $color-theme
  font-size: 0
  .logo
    display: inline-block
    vertical-align: top
    margin-top: 6px
    width: 30px
    height: 32px
    margin-right: 9px
    background-image url("./assets/logo@2x.png")
    background-size: 30px 32px
  .title
    display inline-block
    vertical-align top
    margin-top 10px
    font-size 20px
  .mime
    position absolute
    top 0
    right 10px
    font-size 16px
    .myicon
      display block
      padding 12px
      color: $color-theme
</style>
