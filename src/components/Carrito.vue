<template>
    <div>
        <ul class="list-group">
            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{item.titulo}} - {{item.precio}}
                <button class="btn badge badge-danger float-right" @click="removerItem(item)"> Eliminar </button>
            </li>
        </ul>
        <div class="card p-3 my-5">
            <h4 class="text-center"> Total: ${{ total }} </h4>      <!-- total es una propiedad computada -->
        </div>
        <button :disabled="items.length === 0" @click="$emit('pagar')" class="btn btn-info form-control">Pagar ahora</button>   <!-- emite en evento pagar, para que lo pueda capturar App.vue -->
    </div>      <!-- con binding :disabled desahabilita el boton cuando no hallan elementos en el arreglo -->
</template>

<script>
export default {
    name: 'Carrito',
    props: ['items'],        // recibe infotmación de App.vue
    computed: {
        total() {
            return this.items.reduce((acumulador, item) => acumulador + Number(item.precio),0);     //mantiene la suma total
        }                   // función reduce()  utiliza una variable acumulador que va sumando el valor del arreglo item.precio empezando en cero
    },
    methods: {
        removerItem(item){
            this.$emit('remover-item', item);   // crea el evento remover-item y pasa el valor de item al componente padre App.vue
        }
    },
}
</script>