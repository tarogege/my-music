<template>
  <div class="listview">
    <div v-for="(typelist,index) in singerList" :key="index">
      <div class="title">{{typelist.title}}</div>
      <ul class="singerlist">
        <li v-for="(singer,singerindex) in typelist.items" :key="singerindex" class="singeritem">
          <div class="avatar">头像</div>
          <div class="name">{{singer.name}}</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    singerList: {
      type: Array,
      default: () => {
        return []
      }
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
.listview
  .title
    background-color #7e8c8d
  .singerlist
    .avatar
      font-size: $font-size-small
      color: $color-text-l
      background: $color-highlight-background
    .singeritem
      padding 20px 10px
      border-bottom 1px solid #7e8c8d
</style>
