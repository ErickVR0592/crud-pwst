<template>
  <div class="">
    <h1 class="title is-size-3 has-text-white">{{ msg }}</h1>
    <div class="card">
      <div class="card-content">
        <img alt="PSWT logo" src="../assets/logo-powerstreet.png">
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="email" placeholder="Usuario" required v-model="user" @keypress.enter="login">
            <span class="icon is-small is-left">
              <i class="fas fa-user"></i>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="password" placeholder="Contraseña" required v-model="password" @keypress.enter="login">
            <span class="icon is-small is-left">
              <i class="fas fa-lock"></i>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control">
            <a @click="login" class="button is-success">
              Login
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  
  name: 'Login',
  data() {
    return{
      user: "",
      password: ""
    }
  },
  props: {
    msg: String
  },
  methods: {
    login(){
      // const socket = io("http://prueba.pwstasp.net/api/conexion_login/login");
      // socket.on("connect", () => {
      //   console.log(socket.connected); // true
      // });


      var url = 'http://prueba.pwstasp.net/api/conexion_login/login',
        params = {
          method: 'POST',
          mode: 'cors',
          body: JSON.stringify({ 'usuario': this.user, 'contrasenia': this.password }),
          headers: { 'Content-Type': 'application/json' },
        };

      var request = new Request(url, params);

      fetch(request)
        .then(res => res.json())
        .then(res => {
          // console.log(res)
          //si el usuario existe.
          if (res.exito == true) {
            localStorage.login = res.exito
            this.$router.push('dashboard')
          } else {
            alert("Usuario y/o contraseña incorrectos")
          }
        })
        .catch((err) => {
          console.log(err)
          return "error";
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
