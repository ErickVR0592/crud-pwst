<template>
  <div class="login">
    <!-- <img alt="Vue logo" src="../assets/logo-powerstreet.png"> -->
    <section class="hero is-fullheight">
      <div class="hero-body is-flex is-justify-content-center">
        <Login msg="Bienvenido"/> 
      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import Login from '@/components/Login.vue'

export default {
  name: 'HomeLogin',
  components: {
    Login
  }
}
</script>

<style scoped>
.hero{
  background-image: url('../assets/background.jpg');
  background-position-x: 75%;
  background-position-y: 15%;
}
</style>
