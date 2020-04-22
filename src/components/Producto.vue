<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-title">{{producto.titulo}}</h5>
            <img :src="producto.imagen" width="290" height="150">       <!-- se hace un binding para mandar información a la propiedad src, -->
            <p class="text-center text-muted card-text display-4">$ {{ Number(producto.precio).toFixed()}}</p>  <!-- información recibida con props  -->
            <button @click="agregarCarro(producto)" class="btn btn-primary form-control" :disabled="estaEnCarrito">
                {{ estaEnCarrito ? 'Agregado' : 'Agregar al carrito' }}
            </button>    <!-- se envía la información del producto al padre App.vue  /  se deshabilita boton si es true -->
        </div>      
    </div>
</template>

<script>
export default {
    name: 'Producto',
    props: ['producto', 'estaEnCarrito'],     // en props recibe los datos desde App.vue como un arreglo 
    methods:{                                 // estaEnCarrito recibirá un true o false desde App.vue
        agregarCarro(producto){                      
            this.$emit('agregar-carro', producto);  // emisión del evento para enviar información del producto a App.vue con el nombre agregar-carro
        }
    }
}
</script>

<style>
</style>