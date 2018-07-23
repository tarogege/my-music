<template>
<div class="singer">
  <listview :singerList="singerList"></listview>
</div>
</template>

<script type="text/ecmascript-6">
import { getSingerList } from '../../api/singers'
import Listview from '../../base/listview/listview'

const HOT_NAME = '热门'
const HOT_NUM = 10
export default {
  data () {
    return {
      singerList: []
    }
  },
  components: {
    listview: Listview
  },
  methods: {
    _getSingerList() {
      getSingerList().then((res) => {
        if (res.code === 0) {
          this.singerList = res.data.list
          console.log(this.singerList)
          this.singerList = this._normalizeSingerList(this.singerList)
        }
      })
    },
    _normalizeSingerList(list) {
      let map = {
        hot: {
          title: HOT_NAME,
          items: []
        }
      }
      list.forEach((item, index) => {
        if (index < HOT_NUM) {
          map.hot.items.push({
            id: item.Fsinger_mid,
            name: item.Fsinger_name
          })
        }

        let key = item.Findex
        if (!map[key] && key !== '9') {
          map[key] = {
            title: key,
            items: []
          }
        }
        if (key === '9') {
          key = '#'
          map[key] = {
            title: key,
            items: []
          }
        }
        map[key].items.push({
          id: item.Fsinger_mid,
          name: item.Fsinger_name
        })
      })

      //  对map进行排序
      let ret = []
      let hot = []
      for (let key in map) {
        let val = map[key]
        if (val.title.match(/[a-zA-Z]/)) {
          ret.push(val)
        } else if (val.title === HOT_NAME) {
          hot.push(val)
        }
      }
      ret.sort((a, b) => {
        return a.title.charCodeAt(0) - b.title.charCodeAt(0)
      })
      return hot.concat(ret)
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
