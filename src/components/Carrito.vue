<template>
    <div>
        <ul class="list-group">
            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{item.titulo}} - {{item.precio}}
                <button class="btn badge badge-danger float-right" @click="removerItem(item)"> Eliminar </button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Carrito',
    props: ['items'],        // recibe infotmación de App.vue
    methods: {
        removerItem(item){
            this.$emit('remover-item', item);   // crea el evento remover-item y pasa el valor de item al componente padre App.vue
        }
    },
}
</script>