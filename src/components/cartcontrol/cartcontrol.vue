<template>
  <div class="cartcontrol">
    <transition  name="move">
      <div class="cart-decrease"  v-show="food.count>0" @click.stop.prevent="decreaseCart">
        <span class="inner icon-ali-offline_fill"></span>
      </div>
    </transition>
    <div class="cart-count" v-show="food.count>0" >{{food.count}}</div>
    <div class="cart-add icon-ali-addition_fill" @click.stop.prevent="addCart">

    </div>
  </div>
</template>
<script type="text/ecmascript-6">
 import Vue from 'vue';
export default{
  props: {
      food: {
        type: Object
      }
    },
    methods: {
      addCart(event) {
       if (!event._constructed) {
          return;
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count++;
        }
      },
      decreaseCart(event) {
        if (!event._constructed) {
          return;
        }
        if (this.food.count) {
          this.food.count--;
        }
      }
      }

}


</script>
<style>

  .cartcontrol{
    font-size: 0;
  }
  .cartcontrol .cart-decrease{
    padding: 6px;
    float: left;

  }
  .cartcontrol .cart-decrease .inner{
    display: inline-block;
    line-height: 24px;
    font-size: 24px;
    color: rgb(0, 160, 220);
    transition: all 0.4s linear;
    transform: rotate(-180deg);
    opacity: 1;
  }
  .move-enter-active{
    transition: all 0.4s linear;
  }
  .move-leave-active{
    opacity: 0;
    transition: all 0.4s linear;
    transform: translate3d(24px, 0, 0);
  }
  .cartcontrol .cart-add{
    display: inline-block;
    padding: 6px;
    line-height: 24px;
    font-size: 24px !important;
    float: left;
    color: rgb(0, 160, 220);
  }
  .cartcontrol .cart-count{
    display: inline-block;
    vertical-align: top;
    width: 12px;
    padding-top: 6px;
    line-height: 24px;
    text-align: center;
    font-size: 16px;
    color: rgb(147, 153, 159);
    float: left;
  }

</style>
