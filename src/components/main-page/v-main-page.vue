<template>
   <div class="v-main-page">
      <h1>Online Shop</h1>
      <p>
         <router-link :to="{name:'catalog'}">
            to Catalog
         </router-link>
      </p>
   </div>
</template>
<script>
export default {
   name:'v-main-page'
}
</script>
<style lang="">
   
</style>