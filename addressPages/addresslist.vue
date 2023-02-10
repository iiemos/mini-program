<template>

  <view class="components-list tn-safe-area-inset-bottom">

    <!-- 顶部自定义导航 -->
    <tn-nav-bar fixed>列表</tn-nav-bar>

    <!-- 页面内容 -->
    <view :style="{paddingTop: vuex_custom_bar_height + 'px'}">
      <view class="list_warp">
        <view>
          <tn-list-cell>
            普通列表
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell :radius="true">
            圆角列表
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-icon-text">
              <view class="list__left">
                <view class="list__left__icon tn-icon-discover tn-color-gray"></view>
                <view class="list__left__text">图标 + 文字</view>
              </view>
            </view>
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-image-text">
              <view class="list__left">
                <image src="/static/favicon.ico" class="list__left__image"></image>
                <view class="list__left__text">图片 + 文字</view>
              </view>
            </view>
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-icon-text">
              <view class="list__left">
                <view class="list__left__icon tn-icon-order tn-color-indigo"></view>
                <view class="list__left__text">文本</view>
              </view>
              <view class="list__right">
                <view class="tn-text-sm tn-color-gray">定一个小目标吧</view>
              </view>
            </view>
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-icon-text">
              <view class="list__left">
                <view class="list__left__icon tn-icon-upload tn-color-cyan"></view>
                <view class="list__left__text">按钮</view>
              </view>
              <view class="list__right">
                <tn-button backgroundColor="#01BEFF" fontColor="#FFFFFF" shape="round" size="sm">
                  <text class="tn-icon-upload tn-margin-right-xs"></text>上传
                </tn-button>
              </view>
            </view>
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-icon-text">
              <view class="list__left">
                <view class="list__left__icon tn-icon-tag tn-text-clip tn-main-gradient-orangeyellow"></view>
                <view class="list__left__text">标签</view>
              </view>
              <view class="list__right">
                <tn-tag backgroundColor="tn-main-gradient-indigo" shape="circle" margin="0rpx 5rpx">篮球</tn-tag>
                <tn-tag backgroundColor="tn-main-gradient-indigo" shape="circle" margin="0rpx 5rpx">足球</tn-tag>
                <tn-tag backgroundColor="tn-main-gradient-indigo" shape="circle" margin="0rpx 5rpx">小球</tn-tag>
              </view>
            </view>
          </tn-list-cell>
        </view>
        <view class="tn-margin-top-sm">
          <tn-list-cell>
            <view class="list-icon-text">
              <view class="list__left">
                <view class="list__left__icon tn-icon-emoji-good tn-text-clip tn-main-gradient-orangered"></view>
                <view class="list__left__text">头像组</view>
              </view>
              <view class="list__right">
                <tn-avatar-group :lists="avatarGroupList" size="sm"></tn-avatar-group>
              </view>
            </view>
          </tn-list-cell>
        </view>
      </view>
      
      <view class="tn-padding-bottom-lg"></view>

    </view>

  </view>

</template>

<script>
  export default {
    name: 'addressList',
    data() {
      return {
        showListOptions: false,
        cellShowBorderLine: true,
        cellLongBorderLine: false,
        cellNoPaddingArrow: false,
        
        cellArrow: false,
        cellArrowRight: true,
        cellUnlined: false,
        cellLineLeft: true,
        cellLineRight: true,
        
        avatarGroupList: [
          {src: 'https://tnuiimage.tnkjapp.com/avatar/xiaomai1.jpg'},
          {src: 'https://tnuiimage.tnkjapp.com/avatar/xiaomai2.jpg'},
          {src: 'https://tnuiimage.tnkjapp.com/avatar/xiaomai1.jpg'},
          {src: 'https://tnuiimage.tnkjapp.com/avatar/xiaomai2.jpg'},
        ]
      }
    },
    watch: {
      cellShowBorderLine(val) {
        if (val) {
          this.cellUnlined = false
        } else {
          this.cellUnlined = true
        }
      },
      cellLongBorderLine(val) {
        if (val) {
          this.cellLineLeft = false
          this.cellLineRight = false
        } else {
          this.cellLineLeft = true
          this.cellLineRight = true
        }
      },
      cellNoPaddingArrow(val) {
        if (val) {
          this.cellArrowRight = false
        } else {
          this.cellArrowRight = true
        }
      }
    },
    methods: {
      // 弹出设置弹框
      openOptions() {
        this.showListOptions = true
      },
      // 关闭设置弹框
      closeOptions() {
        this.showListOptions = false
      }
    }
  }
</script>

<style lang="scss" scoped>
  .list_warp{
    margin-top: 30rpx;
    margin-left: 30rpx;
    margin-right: 30rpx;
  }
  .components-list {
    background-color: $tn-bg-gray-color;
    min-height: 100vh;
  }
  
  .custom-title {
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
    padding: 10rpx 20rpx;
  }
  
  .list__options {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .list {
    &__left {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      
      &__icon, &__image {
        margin-right: 18rpx;
      }
    }
    
    &__right {
      display: flex;
      align-items: center;
      justify-content: flex-end;
    }
  }
  
  .list-icon-text, .list-image-text {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .list-image-text {
    .list {
      &__left {
        &__image {
          width: 20rpx;
          height: 20rpx;
        }
      }
    }
  }
  
  .message {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    
    &__left {
      width: 10%;
    }
    &__middle {
      width: 80%;
      padding-left: 20rpx;
      padding-right: 40rpx;
    }
    &__right {
      width: 10%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    
    &__name {
      font-size: 32rpx;
      margin-bottom: 8rpx;
    }
    &__content {
      font-size: 26rpx;
      color: #838383;
    }
    &__tips {
      &__icon {
        font-size: 36rpx;
        color: #AAAAAA;
      }
    }
  }
</style>
