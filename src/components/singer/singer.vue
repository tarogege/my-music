<template>
<div class="singer">singer</div>
</template>

<script type="text/ecmascript-6">
import { getSingerList } from '../../api/singers'

export default {
  data () {
    return {
      singerList: []
    }
  },
  methods: {
    _getSingerList() {
      getSingerList().then((res) => {
        console.log(res)
        if (res.code === 0) {
          this.singerList = res.data.list
        }
      })
    }
  },
  created() {
    console.log('lallalll')
    this._getSingerList()
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">

</style>
