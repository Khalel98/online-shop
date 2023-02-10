<template lang="">
   <div class="v-catalog-item">

      <v-popup 
         v-if="isInfoPopupVisible"
         rightBtnTitle="Add to cart"
         :popupTitle="product_data.title"
         @closePopup="closeInfoPopup"
         @rightBtnAction="addToCart"

      >
         <div class="popup__img">
            <img v-bind:src="product_data.thumbnail" alt="img">
         </div>
         <div class="popup__text">
            <p class="v-catalog-item__name">{{ product_data.description}}</p>
            <p class="v-catalog-item__price">Price: {{ product_data.price}}</p>
            <p class="v-catalog-item__price">Category: {{ product_data.category}}</p>
         </div>
      </v-popup>

      <div class="v-catalog-item__image">
         <img class="v-catalog-item__image" v-bind:src="product_data.thumbnail" alt="img">
      </div>
      <p class="v-catalog-item__name">{{ product_data.title}}</p>
      <p class="v-catalog-item__price">Price: {{ product_data.price}}</p>
      <div class="btns">
         <button class="v-catalog-item__add_to_cart_btn btn" @click="addToCart">Add to cart</button>

         <button
            class="v-catalog-item__show-info"
            @click="showPopupInfo"
         >Show info</button>
      </div>
   </div>
</template>
<script>
import vPopup from './popup/v-popup.vue';

export default {
   name: 'v-catalog-item',
   components:{
      vPopup
   },
   props:{
      product_data:{
         type:Object,
         default(){
            return{}
         }
      }
   },
   data(){
      return{
         isInfoPopupVisible:false
      }
   },
   methods:{
      showPopupInfo(){
         this.isInfoPopupVisible = true
      },
      closeInfoPopup(){
         this.isInfoPopupVisible = false
      },
      addToCart(){
         this.$emit('addToCart',this.product_data)
      }
   },
   mounted(){
      this.$set(this.product_data,'quantity',1)
   }

}
</script>
<style lang="scss">
   .v-catalog-item{
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 0 8px 0 #e0e0e0;
      padding: 30px 16px;
      margin-bottom: 30px;
      height:300px;
      width:262px;
   }
   .popup__img{
      img{
         width: 100px;
      }
   }

   .popup__text{
      width: 60%;
      font-size: 15px;
   }
   .v-catalog-item__image{
      max-width: 100px;
      max-height: 100px;
      img{
         // max-width: 100px;
         height:100%;
      }
   }

</style>