<template>
  <div id="app">
    <myheader></myheader>
    <tab></tab>
    <router-view/>
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
</style>
