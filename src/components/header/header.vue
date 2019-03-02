<template>
<div class="header">
  <div class="content-wrapper">
    <div class="avatar">
      <img width="64" height="64" :src="seller.avatar" alt="">
    </div>
    <div class="content">
      <div class="title">
        <span class="brand"></span>
        <span class="name">{{ seller.name }}</span>
      </div>
      <div class="description">
        {{seller.description}} / {{seller.deliveryTime}}分钟送达
      </div>
      <div class="support" v-if="seller.supports">
        <span class="icon" :class="classMap[seller.supports[0].type]"></span>
        <span class="text">{{seller.supports[0].description}}</span>
      </div>
    </div>
  </div>
  <div class="bulletin-wrapper"></div>

</div>
</template>

<script>
  export default{
    props: {
      seller: {
        type: Object
      }
    },
    created() {
      this.classMap = [
        'decrease', 
        'discount',
        'special', 
        'invoice',
        'guarantee']
    }
  }
</script>

<style scoped lang="stylus">
@import '../../common/stylus/mixin.styl'
.header 
  background: black
  color: #fff
  .content-wrapper 
    padding: 24px 12px 18px 24px
    font-size: 0
    .avatar 
      display: inline-block
      vertical-align: top
      img
        border-radius: 2px
    .content 
      display: inline-block
      font-size: 14px
      margin-left: 16px
      .title
        margin: 2px 0 8px 0
        .brand 
          display: inline-block
          width: 30px
          height: 18px
          vertical-align: top
          bg-image('brand')
          background-size: 30px 18px
          background-repeat: no-repeat
        .name 
          margin-left: 6px
          font-size: 16px
          line-height: 18px
          font-weight: bold
      .description
        margin-bottom: 10px
        line-height: 12px
        font-size: 12px
      .support
        margin-bottom: 2px;
        font-size: 0
        .icon
          display: inline-block
          width: 12px
          height: 12px
          margin-right: 4px
          vertical-align: top
          background-size: 12px 12px
          background-repeat: no-repeat
          &.decrease
            bg-image('decrease_1')
          &.discount
            bg-image('discount_1')
          &.guarantee
            bg-image('guarantee_1')
          &.invoice
            bg-image('invoice_1')
          &.special
            bg-image('special_1')
        .text
          line-height: 12px
          font-size: 10px
          
</style>
