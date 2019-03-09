<template>
  <div class="cartcontrol">
    <div class="cart-decrease" v-show="food.count>0" @click="decCart" transition="move">
      <i class="icon icon-remove_circle_outline"></i>
    </div>
    <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  props: {
    food: {
      type: Object
    }
  },
  methods: {
    addCart(event) {
      if (!event._constructed) {
        return
      }
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1)
      } else {
        this.food.count ++
      }
      this.$dispatch('cart.add', event.target)
    },
    decCart(event) {
      if (!event._constructed) {
        return 
      }
      if (this.food.count) {
        this.food.count --
      }
    }
  },
  created() {
  }
}
</script>

<style lang="stylus" scoped>
  .cartcontrol
    font-size: 0
    .cart-decrease
      display: inline-block
      padding: 6px
      transition: all 0.4s linear
      .icon
        display: inline-block
        line-height: 24px
        font-size: 24px
        color: rgb(0, 160, 220)
        transition: all 0.4s linear
        transform: rotate(0)
      &.move-transition
        opacity: 1
        transform: translate3d(0,0,0)
      &.move-enter, &.move-leave
        opacity: 0
        transform: translate3d(24px, 0, 0)
        .icon
          transform: rotate(188deg)
    .cart-count
      display: inline-block
      vertical-align: top
      width: 12px
      padding-top: 6px
      line-height: 24px
      text-align: center
      font-size: 10px
      color: rgb(147, 153, 159)
    .cart-add
      display: inline-block
      padding: 6px
      line-height: 24px
      font-size: 24px
      color: rgb(0, 160, 220)
</style>


