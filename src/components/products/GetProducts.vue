<template>
  <div>
    <modal-details
      :active="showModalMessage"
      :close="closeModal"
      :img="img"
      :description="description"
      :name="name"
    />

    <div class="card">
      <div class="card-image">
        <figure class="image is-4by3">
          <img :src="img" alt="Placeholder image">
        </figure>
      </div>
      <div class="card-content">
        <div class="media is-flex is-align-items-center">
          <div class="media-content is-flex is-flex-direction-column is-align-items-flex-start">
            <p class="title is-4">{{name}}</p>
            <p class="subtitle is-6"><a @click="openModal">Detalle</a></p>
          </div>
          <div class="media-left">
            <p class="subtitle is-6">${{price}}.00</p>
          </div>
        </div>

        <div class="content">
          <div class="buttons is-flex is-justify-content-space-around">
            <button class="button is-success" @click="addProduct">Agregar</button>
            <button class="button is-danger">Quitar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ModalDetails from './ModalDetails.vue'
export default {
  components: { ModalDetails },
  name: 'GetProducts',
  data(){
    return {
      showModalMessage: false,
    }
  },
  props: {
    img: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
    addProduct: {
      type: Function
    }
  },
  methods: {
    closeModal () {
      this.showModalMessage = !this.showModalMessage
    },
    openModal () {
      this.showModalMessage = !this.showModalMessage
    },
  },
}
</script>

<style>

</style>