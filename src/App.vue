<template>
  <div id="app">

    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="prod in productos" :key="prod.id">   <!-- recorrido de arreglo de objetos productos.json -->
            <producto :producto="prod" v-on:agregar-carro="agregarProdCarro" :estaEnCarrito="estaEnCarrito(prod)"></producto>      <!-- manda un objeto de información del producto al componente hijo Producto.vue que lo recibe atravéz de props-->
          </div>                   <!-- captura evento agregar-carro desde Producto.vue   // props estaEnCarrito recibe del método un true o false y es enviado -->
        </div>
      </div>

      <div class="col-md5 my-5">
        <carrito :items="carrito"></carrito>    <!-- se envía al props items el objeto carrito -->
      </div>
    </div>
  </div>
</template>

<script>
import productos from './productos.json'          //importación de achivo .json
import Producto from './components/Producto.vue'
import Carrito from './components/Carrito.vue'

export default {
  name: 'App',
  components: {
    Producto,
    Carrito    
  },
  data() {
    return {
      productos,                                   // datos archivo productos.json
      carrito: []     // arreglo en forma general
    }
  },
  methods: {
    agregarProdCarro(producto){
      this.carrito.push(producto);    //  se agrega el objeto producto
    },
    estaEnCarrito(producto){
      const item = this.carrito.find(item => item.id === producto.id);  // comprueba si existe ese id en el carrito
      if (item){
        return true;
      }
      return false;
    }
  },
}
</script>


<style>

</style>
