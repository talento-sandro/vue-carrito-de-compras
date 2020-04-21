<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-title">{{producto.titulo}}</h5>
            <img :src="producto.imagen" width="290" height="150">       <!-- se hace un binding para mandar información a la propiedad src -->
            <p class="text-center text-muted card-text display-4">$ {{ Number(producto.precio).toFixed()}}</p>
            <button class="btn btn-primary form-control">Agregar al carrito</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Producto',
    props: ['producto']             // en props recibe datos como un arreglo 
}
</script>

<style>
</style>