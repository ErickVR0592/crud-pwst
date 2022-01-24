<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand is-flex is-align-items-center">
      <router-link class="navbar-item" to="/dashboard">
        <img src="../assets/logo-powerstreet.png">
      </router-link>

      <a @click="menu" role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navMenu">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navMenu" class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item">
          <span class="icon is-small is-left mr-4">
            <i class="fas fa-user"></i>
          </span>
          <p class="mr-4"><strong>Hola</strong> Pablo</p>
          <router-link to="/" class="button is-link">
            <strong>Cerrar sesión</strong>
          </router-link>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  methods: {
    menu () {
      let burger = document.querySelector('.navbar-burger')
      let nav = document.querySelector('#'+burger.dataset.target)
      burger.classList.toggle('is-active')
      nav.classList.toggle('is-active')
    }
  }
}
</script>

<style>
.navbar-item img{
  max-height: 4.75rem;
}
</style>