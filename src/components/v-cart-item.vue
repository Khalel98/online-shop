<template lang="">
   <div class="v-cart-item">
      <img class="v-cart-item__image" v-bind:src="cart_item_data.thumbnail" alt="img">
      <div class="v-cart-item__info">
         <p>{{cart_item_data.title}}</p>
         <p>{{cart_item_data.price}}</p>
         <p>{{cart_item_data.brand}}</p>
      </div>
      <div class="v-cart-item__quantity">
         <span class="quantity__tools">
            <span class="quantity__btn" @click="decrementItem">-</span>
            {{cart_item_data.quantity}}
            <span class="quantity__btn" @click="incrementItem">+</span>
         </span>
      </div>
      <button @click="deleteFromCart">Delete</button> 

   </div>
</template>
<script>


export default {
   name: "v-cart-item",
   props:{
      cart_item_data:{
         type:Object,
         default(){
            return {}
         }
      }
   },
   methods:{
      decrementItem() {
        this.$emit('decrement')
      },
      incrementItem() {
        this.$emit('increment')
      },
      deleteFromCart(){
         this.$emit('deleteFromCart')
      }
   }
}
</script>
<style>
   .v-cart-item{
      display:flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: nowrap;
      box-shadow: 0 0 8px 0 #e0e0e0;
      padding: 16px;
      margin-bottom: 16px;
   }
   .v-cart-item__image{
      max-width:100px;
   }
   .quantity__btn {
      cursor: pointer;
    }
    .quantity__tools {
      user-select: none;
    }
</style>