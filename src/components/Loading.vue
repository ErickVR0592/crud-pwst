<template>
  <div class="columns is-multiline loading-component">
    <div class="column is-12 has-text-centered is-flex is-flex-direction-column is-align-items-center">
      <img src="../assets/logo-powerstreet.png" alt="PSWT logo">
      <i class="fas fa-spinner"></i>
    </div>
    <div class="column is-12">
      <div class="loading">
      </div>
    </div>
  </div>
</template>

<style scoped>
.loading-component {
  margin-top: 150px;
}
img {
  width: 250px;
}
.fa-spinner{
  animation-name: rotate-loading;
  animation-duration: 2s; 
  animation-iteration-count: infinite; 
  animation-timing-function: linear; 
}

@keyframes rotate-loading{
  from{
    transform: rotateZ(0deg);
  }
  to{
    transform: rotateZ(360deg);
  }
}
</style>