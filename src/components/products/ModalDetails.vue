<template>
  <div class="modal is-active" v-if="active">
    <div class="modal-background"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">{{name}}</p>
        <button class="delete" aria-label="close" @click="close"></button>
    </header>
    <section class="modal-card-body">
      <img :src="img" alt="placeholder image">
      <div class="desciption">
        {{description}}
      </div>
    </section>
    </div>
    <!-- <button class="modal-close is-large" aria-label="close" @click="close"></button> -->
  </div>
</template>
-->

<script>
export default {
  props: {
    active: Boolean,
    close: {
      type: Function
    },
    img: {
      type: Object
    },
    description: {
      type: Object
    },
    name:{
      type: Object
    }
  }
}
</script>

<style scoped>
  .modal-card-head {
    background-color: #12497c;
  }
  .modal-card-title {
    text-align: center;
    color: #FFF;
    text-transform: uppercase;
  }
  .modal-card-body {
    background-color: #eeeeee;
    border-bottom-left-radius: 6px;
    border-bottom-right-radius: 6px;
  }
</style>