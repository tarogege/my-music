<template>
  <div class="recommend">
    <scroll :data="dissList" class="recommend-content" ref="scrollWrapper">
      <div>
        <div class="slider-wrapper">
          <div class="slider-content">
            <slider v-if="recommends.length">
              <div v-for="(recommend, index) in recommends" :key="index">
                <a :href="recommend.linkUrl">
                  <img v-lazy="recommend.picUrl" @load="loadImg()" class="needsclick">
                </a>
              </div>
            </slider>
          </div>
        </div>
        <div class="recommend-list">
          <h2>热门歌曲推荐</h2>
          <div>
            <div class="recommendul">
              <ul>
                <li v-for="(disc, index) in dissList" :key="index">
                  <a>
                    <div class="discItem">
                      <div class="rightAvatar"><img :src="disc.imgurl" class="avatarImg"></div>
                      <div class="leftWrapper">
                        <p class="discCreator">{{disc.creator.name}}</p>
                        <p class="discname">{{disc.dissname}}</p>
                      </div>
                    </div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="loading-container" v-show="!dissList.length"><loading></loading></div>
    </scroll>
  </div>
</template>

<script type="text/ecmascript-6">
import { getRecommend, getDiscList } from '../../api/recommend'
import { ERR_OK } from '../../api/config'
import Slider from '../../base/slider'
import Scroll from '../../base/scroll'
import Loading from '../../base/loading.vue'
export default {
  components: {
    slider: Slider,
    scroll: Scroll,
    loading: Loading
  },
  data() {
    return {
      recommends: [],
      dissList: []
    }
  },
  created() {
    this._getRecommend()
    setTimeout(this._getDiscList(), 2000)
  },
  methods: {
    loadImg() {
      if (!this.checkLoaded) {
        this.$refs.scrollWrapper.refresh()
        this.checkLoaded = true
      }
    },
    _getDiscList() {
      getDiscList().then((res) => {
        if (res.code === ERR_OK) {
          this.dissList = res.data.list
        }
      })
    },
    _getRecommend() {
      getRecommend().then((res) => {
        if (res.code === ERR_OK) {
          this.recommends = res.data.slider
        }
      })
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import '../../common/stylus/variable.styl'
.recommend
  position fixed
  width 100%
  top 88px
  bottom 0
  .recommend-content
    height 100%
    overflow: hidden
    .slider-wrapper
      position: relative
      width: 100%
      height 0
      padding-top 40%
      overflow hidden
      .slider-content
        position: absolute
        top: 0
        left: 0
        width: 100%
        height: 100%
    .recommend-list
      margin-top 20px
      text-align center
      color $color-theme
      .recommendul
        margin-top 15px
        .discItem
          display flex
          padding 0 20px 10px
          .rightAvatar
            flex  0 0 60px
            width 60px
            .avatarImg
              width 60px
              height 60px
          .leftWrapper
            flex 1
            display flex
            flex-direction column
            text-align left
            padding-left 10px
            .discCreator
              flex 1
              color white
            .discname
              flex 1
    .loading-container
      position absolute
      width 100%
      top 50%
      transform: translateY(-50%)
</style>
