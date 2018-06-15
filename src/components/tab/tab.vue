<template>
<div class="tab">
  <router-link to="/recommend" class="link-r recommend">推荐</router-link>
  <router-link to="/singer" class="link-r singer">歌手</router-link>
  <router-link to="/rank" class="link-r rank">排行</router-link>
  <router-link to="/search" class="link-r search">搜索</router-link>
</div>
</template>

<script type="text/ecmascript-6">
export default {}
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/variable.styl"
.tab
  display flex
  text-align center
  .link-r
    flex 1
    text-decoration none
    color $color-text-l
    &.link-r-active
      color $color-theme
</style>
