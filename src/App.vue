<template>
  <div id="app">
    <myheader></myheader>
    <tab></tab>
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script>
import header from './components/m-header/m-header'
import tab from './components/tab/tab'
export default {
  name: 'App',
  components: {
    myheader: header,
    tab: tab
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .app
    background-color black
</style>
