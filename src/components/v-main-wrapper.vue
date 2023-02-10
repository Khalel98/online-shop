<template lang="">
   <div class="v-main-wrapper">
      <v-header />
      <keep-alive>
         <router-view>

         </router-view>
      </keep-alive>

   </div>
</template>

<script>
import vHeader from './layout/v-header.vue';
 
export default {
   name:'v-main-wrapper',
   props:{},
   components:{
      vHeader
   },
   data(){
      return{
         title:'Main'
      }
   },
   computed:{},
   methods:{},
   watch:{}

}
</script>

<style >
   .v-main-wrapper{
      max-width: 1000px;
      margin: 0 auto;
   }
</style>