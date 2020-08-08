<template>
  <div class="ebook">
    <title-bar :ifTiTleAndMenuShow="ifTiTleAndMenuShow"></title-bar>
    <div class="read-wrapper">
      <div id="read"></div>
      <div class="mask">
        <div class="left" @click="prevPage"></div>
        <div class="center" @click="toggleTitleAndMenu"></div>
        <div class="right" @click="nextPage"></div>
      </div>
    </div>
    <menu-bar :ifTiTleAndMenuShow="ifTiTleAndMenuShow"></menu-bar>
  </div>
</template>

<script>
import TitleBar from '@/components/TitleBar'
import MenuBar from '@/components/MenuBar'
import Epub from 'epubjs'
const DOWNLOAD_URL = '/static/09F3.epub'
global.ePub = Epub
export default {
  components: {
    TitleBar,
    MenuBar
  },
  data () {
    return {
      ifTiTleAndMenuShow: false
    }
  },
  methods: {
    toggleTitleAndMenu () {
      this.ifTiTleAndMenuShow = !this.ifTiTleAndMenuShow
    },
    prevPage () {
      if (this.rendition) {
        this.rendition.prev()
      }
    },
    nextPage () {
      if (this.rendition) {
        this.rendition.next()
      }
    },
    showEpub () {
      this.book = new Epub(DOWNLOAD_URL)
      this.rendition = this.book.renderTo('read', {
        width: window.innerWidth,
        height: window.innerHeight
      })
      this.rendition.display()
    }
  },
  mounted () {
    this.showEpub()
  }
}
</script>

<style lang='scss' scoped>
@import 'assets/styles/global';
.ebook {
  position: relative;
  .read-wrapper {
    .mask {
      position: absolute;
      top: 0;
      left: 500;
      z-index:100;
      display: flex;
      width:100%;
      height: 100%;
      .left {
        flex: 0 0 px2rem(100);
      }
      .center {
        flex: 1;
      }
      .right {
        flex: 0 0 px2rem(100);
      }
    }
  }
}
</style>
