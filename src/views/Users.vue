<template>
  <div>
    <Header/>
    <a class="button is-info mb-6" onclick="window.history.back()">Go back</a>
  </div>
</template>

<script>

import Header from '../components/Header.vue'
  export default {
  name: 'Users',
  components: { Header },
    
  }
</script>

<style scoped>

</style>