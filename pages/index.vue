<template>
  <view class="start-index">
    <view v-if="tabberPageLoadFlag[0]" :style="{display: currentIndex === 0 ? '' : 'none'}">
      <scroll-view class="custom-tabbar-page" scroll-y enable-back-to-top @scrolltolower="tabbarPageScrollLower">
        <home ref="home"></home>
      </scroll-view>
    </view>
    <view v-if="tabberPageLoadFlag[1]" :style="{display: currentIndex === 1 ? '' : 'none'}">
      <scroll-view class="custom-tabbar-page" scroll-y enable-back-to-top @scrolltolower="tabbarPageScrollLower">
        <address-page ref="circleRef"></address-page>
      </scroll-view>
    </view>
    <view v-if="tabberPageLoadFlag[2]" :style="{display: currentIndex === 2 ? '' : 'none'}">
      <scroll-view class="custom-tabbar-page" scroll-y enable-back-to-top @scrolltolower="tabbarPageScrollLower">
        <activity ref="activity"></activity>
      </scroll-view>
    </view>
    <view v-if="tabberPageLoadFlag[3]" :style="{display: currentIndex === 3 ? '' : 'none'}">
      <scroll-view class="custom-tabbar-page" scroll-y enable-back-to-top @scrolltolower="tabbarPageScrollLower">
        <preferred ref="preferredRef"></preferred>
      </scroll-view>
    </view>
    <view v-if="tabberPageLoadFlag[4]" :style="{display: currentIndex === 4 ? '' : 'none'}">
      <scroll-view class="custom-tabbar-page" scroll-y enable-back-to-top @scrolltolower="tabbarPageScrollLower">
        <mine ref="mine"></mine>
      </scroll-view>
    </view>
    
    <tn-tabbar
      v-model="currentIndex"
      :list="tabbarList"
      activeColor="#7c3aed"
      inactiveColor="#AAAAAA"
      activeIconColor="#7c3aed"
      :animation="true"
      :safeAreaInsetBottom="true"
      @change="switchTabbar"
    ></tn-tabbar>
  </view>
</template>

<script>
  import Home from './home/home.vue'
  import AddressPage from './address/address.vue'
  import Activity from './activity/activity.vue'
  import Preferred from './preferred/preferred.vue'
  import Mine from './mine/mine.vue'
  
  export default {
    components: {
      Home,
      AddressPage,
      Activity,
      Preferred,
      Mine
    },
    data() {
      return {
        // ??????tabbar????????????
        tabbarList: [
          {
            title: '??????',
						iconSize: 44,
            activeIcon: 'home-smile-fill',
            inactiveIcon: 'home-smile'
          },
					{
					  title: '?????????',
						iconSize: 44,
					  activeIcon: 'order-fill',
					  inactiveIcon: 'order',
					},
          {
            title: '??????',
            activeIcon: 'menu-circle',
            inactiveIcon: 'rocket',
            activeIconColor: '#FFFFFF',
            inactiveIconColor: '#FFFFFF',
            iconSize: 50,
            out: true
          },
					{
            title: '??????',
						iconSize: 44,
            activeIcon: 'discover-fill',
            inactiveIcon: 'discover'
          },
          {
            title: '??????',
						iconSize: 44,
            activeIcon: 'my-fill',
            inactiveIcon: 'my'
          }
        ],
        // tabbar????????????????????????
        currentIndex: 0,
        // ??????????????????????????????????????????
        tabberPageLoadFlag: []
      }
    },
    onLoad(options) {
      const index = Number(options.index || 0)
      // ????????????tabbar?????????????????????????????????????????????
      this.tabberPageLoadFlag = this.tabbarList.map((item, tabbar_index) => {
        return index === tabbar_index
      })
      this.switchTabbar(index)
    },
    methods: {
      // ????????????
      switchTabbar(index) {
        this._switchTabbarPage(index)
        if (index !== 1) {
          this.$refs?.circleRef?.stopAllVideo()
        }
      },
      
      
      // ???????????????????????????
      tabbarPageScrollLower(e) {
        if (this.currentIndex === 3) {
          this.$refs.preferredRef.getRandomData && this.$refs.preferredRef.getRandomData()
        }
      },
      
      // ??????????????????
      _switchTabbarPage(index) {
        const selectPageFlag = this.tabberPageLoadFlag[index]
        if (selectPageFlag === undefined) {
          return
        }
        if (selectPageFlag === false) {
          this.tabberPageLoadFlag[index] = true
        }
        this.currentIndex = index
      }
    }
  }
</script>

<style lang="scss" scoped>
</style>
