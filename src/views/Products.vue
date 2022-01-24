<template>
  <div>
    <Header/>
    <a class="button is-info mb-6" onclick="window.history.back()">Go back</a>
    <ProductList/>
  </div>
</template>

<script>

import Header from '../components/Header.vue'
import ProductList from '../components/products/ProductList.vue'
  export default {
  name: 'Products',
  components: { Header, ProductList },
    
  }
</script>

<style scoped>

</style>