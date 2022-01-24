<template>
  <div>
    <Loading v-if="pageLoading"/>
    <template v-else>
      <div class="container products mt-6">
        <div class="search">
          <section class="panel is-info">
            <p class="panel-heading">
              Buscar Producto
            </p>
            <div class="panel-block pr-6">
              <p class="control has-icons-left">
                <input class="input is-info" type="text" placeholder="Search" v-model="searchProduct" @keypress.enter="search" >
                <span class="icon is-left">
                  <i class="fas fa-search" aria-hidden="true"></i>
                </span>
              </p>
              <span class="icon ml-4">
                  <button class="button ml-5" @click="addProduct"><i class="fas fa-shopping-cart"></i></button>
              </span>
            </div>
          </section>
        </div>
        <div class="columns is-multiline is-desktop mt-6">
          <div class="column is-one-quarter" v-for="(product) in dataPages" :key="product.codigo_producto" >
            <get-products
              :img="product.imagen"
              :name="product.nombre_producto"
              :description="product.descripcion"
              :price="product.precio"
              :addProduct='addProduct'
            />
          </div>
        </div>
        <nav class="pagination is-rounded is-centered mt-6" role="navigation" aria-label="pagination">
          <a class="pagination-previous" @click="getPreviousPage">Anterior</a>
          <a class="pagination-next" @click="getNextPage">Siguiente</a>
          <ul class="pagination-list">
            <li v-for="(page) in totalPages()" :key="page" @click="getDataPage(page)"><a class="pagination-link" v-bind:class="isActive(page)" aria-label="Page" aria-current="page">{{page}}</a></li>
          </ul>
        </nav>
      </div>
    </template>
  </div>
</template>

<script>
import Loading from '../Loading.vue';
import GetProducts from './GetProducts.vue'
export default {
  name: 'ProductList',
  components: { GetProducts, Loading },
  data(){
    return{
      pageLoading: true,
      products: null,
      elements: 10,
      dataPages: [],
      actualPage: 1,
      searchProduct: '',
    }
  },
  props: {
    match: {
      type: String
    }
  },
  mounted() {
    var url = 'http://prueba.pwstasp.net/api/conexion_login/productos',
        params = {
          method: 'POST',
          mode: 'cors',
          body: JSON.stringify({ "limite":20, "pagina":1 }),
          headers: { 'Content-Type': 'application/json' },
        };

      var request = new Request(url, params);

      fetch(request)
        .then(res => res.json())
        .then(res => {
          // console.log(res)
          this.products = res.datos
          this.getDataPage(1)
          return this.pageLoading = false
        })
        .catch((err) => {
          console.log(err)
          return "error";
        })
  },
  methods: {
    totalPages(){
      return Math.ceil(this.products.length / this.elements)
    },
    getDataPage(NoPage){
      this.actualPage = NoPage
      this.dataPages = []
      let start = (NoPage * this.elements) - this.elements
      let end = (NoPage * this.elements)
      for (let i = start; i < end; i++) {
        this.dataPages.push(this.products[i])
        // console.log(this.dataPages)
      }
    },
    getPreviousPage(){
      if (this.actualPage > 1) {
        this.actualPage--
      }
      this.getDataPage(this.actualPage)
    },
    getNextPage(){
      if (this.actualPage < this.totalPages()) {
        this.actualPage++
      }
      this.getDataPage(this.actualPage)
      console.log(this.match);
    },
    isActive(noPage){
      return noPage == this.actualPage ? 'is-current' : ''
    },
    search(){
      var url = 'http://prueba.pwstasp.net/api/conexion_login/productos',
        params = {
          method: 'POST',
          mode: 'cors',
          body: JSON.stringify({ "busqueda":this.searchProduct }),
          headers: { 'Content-Type': 'application/json' },
        };

      var request = new Request(url, params);

      fetch(request)
        .then(res => res.json())
        .then(res => {
          this.dataPages = res.datos
          return this.pageLoading = false
        })
        .catch((err) => {
          console.log(err)
          return "error";
        })
    },
    addProduct(){
      alert("Añadido al carrito")

    }
  }

}
</script>

<style>

</style>