<template>
  <div class="">
    <h1 class="title is-size-3 has-text-white">{{ msg }}</h1>
    <div class="card">
      <div class="card-content">
        <img alt="PSWT logo" src="../assets/logo-powerstreet.png">
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="email" placeholder="Usuario">
            <span class="icon is-small is-left">
              <i class="fas fa-user"></i>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="password" placeholder="Contraseña">
            <span class="icon is-small is-left">
              <i class="fas fa-lock"></i>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control">
            <button class="button is-success">
              Login
            </button>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
