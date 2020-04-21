<template>
  <div id="app">

    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="prod in productos" :key="prod.id">   <!-- recorrido de arreglo de objetos productos -->
            <producto :producto="prod"></producto>      <!-- manda objeto información del producto al componente hijo Producto.vue-->
          </div>
        </div>

      </div>
    </div>
    
  </div>
</template>

<script>
import productos from './productos.json'          //importación de achivo .json
import Producto from './components/Producto.vue'

export default {
  name: 'App',
  components: {
    Producto    
  },
  data() {
    return {
      productos                                   // datos archivo productos.json
    }
  },
}
</script>


<style>

</style>
