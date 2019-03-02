<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <a v-link="{path: '/goods'}">商品</a>
      </div>
      <div class="tab-item">
        <a v-link="{path: '/ratings'}">评价</a>
      </div>
      <div class="tab-item">
        <a v-link="{path: '/seller'}">商家</a>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import VHeader from './components/header/header.vue'
export default {
  data() {
    return {
      seller: {}
    }
  },
  created() {
    this.$http.get('/api/seller').then((response) => {
      response = response.body
      if (response.errno === 0) {
        this.seller = response.data
      }
    })
  },
  components: {
    VHeader
  }
}
</script>

<style scoped lang="stylus">
@import './common/stylus/mixin.styl'
.tab 
  display: flex
  position: relative
  width: 100%
  height: 40px
  line-height: 40px
  /* border-bottom: 1px solid rgba(7, 17, 27, 0.1); */
  border-1px(rgba(7,17,27,0.1))
// .tab::after {
//   display: block;
//   position: absolute;
//   left: 0;
//   bottom: 0;
//   width: 100%;
//   border-top: 1px solid rgba(7, 17, 27, 0.1);
//   content: ' ';
// }
.tab-item 
  flex: 1
  text-align: center
  a 
    display: block
    font-size: 14px
    color: rgb(77, 85, 93)
    &.active
      color: rgb(240, 20, 20)
// .tab-item a 
//   display: block;
//   font-size: 14px;
//   color: rgb(77, 85, 93);

// a.active {
//   color: rgb(240, 20, 20);
// }
</style>
