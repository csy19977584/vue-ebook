<template>
    <div class="menu-bar">
      <transition name="slide-up">
        <div class="menu-wrapper" v-show="ifTiTleAndMenuShow">
          <div class="icon-wrapper">
            <span class="icon-menu icon"></span>
          </div>
          <div class="icon-wrapper">
            <span class="icon-progress icon"></span>
          </div>
          <div class="icon-wrapper">
            <span class="icon-bright icon"></span>
          </div>
          <div class="icon-wrapper">
            <span class="icon-a icon">A</span>
          </div>
        </div>
      </transition>
      <div class="setting-wrapper">
        <div class="setting-font-size"></div>
      </div>
    </div>
</template>

<script>
export default {
  props: {
    ifTiTleAndMenuShow: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang='scss' scoped>
@import '../assets/styles/global';
.menu-bar {
  .setting-wrapper {
    position: absolute;
    bottom: px2rem(48);
    left: 0;
    width: 100%;
    height: px2rem(60);
    background: white;
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, .15);
    .setting-font-size {
    }
  }
  .menu-wrapper {
  position: absolute;
  bottom: 0;
  left: 0;
  display: flex;
  z-index:101;
  width: 100%;
  height: px2rem(48);
  background: white;
  box-shadow: 0 px2rem(-8) px2rem(8) rgba(0,0,0,.15);
  .icon-wrapper {
    flex: 1;
    @include center;
    .icon-progress {
      font-size: px2rem(28);
    }
    .icon-bright {
      font-size: px2rem(24);
    }
  }
  }
}
</style>
