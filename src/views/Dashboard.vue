<template>
  <div>
    <Header/>

    <div class="container mt-6">
      <div class="buttons are-large is-flex is-justify-content-center">
        <a class="button is-info is-fullwidth is-rounded" href="/products">Productos</a>
        <a class="button is-success is-fullwidth is-rounded" href="/shopping">Compras</a>
        <a class="button is-warning is-fullwidth is-rounded" href="/users">Usuarios</a>
      </div>
    </div>
  </div>
</template>

<script>

import Header from '../components/Header.vue'
  export default {
  name: 'Dashboard',
  components: { Header },
    
  }
</script>

<style scoped>

</style>
