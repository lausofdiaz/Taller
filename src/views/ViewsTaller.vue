<script lang="ts">
import {ref} from 'vue';
import ComponentsTaller from '../components/ComponentsTaller.vue'
export default{
    name:'ViewsTaller', data(){
        return{
            articulo: '',
            cantidad: 0,
            valor: 0
        }
    }, 
    components:
    {ComponentsTaller },
    methods:{
        
        
    }
}
</script>
<template>
 <section class="form-container">
    <h2>Articulo</h2>
    <input type="text" v-model="articulo">
    <h2>Cantidad</h2>
    <input type="number" v-model="cantidad">
    <h2>Valor Unitario</h2>
    <input type="text" v-model="valor">
    <button>Agregar</button>
    <ComponentsTaller :articulo="articulo" :cantidad="cantidad" :valor="valor "/>
</section>
</template>

<style scoped>
.form-container {
            width: 300px;
            text-align: left;
        }
        .form-container h2 {
            margin-bottom: 5px;
        }
        .form-container input {
            width: 100%;
            margin-bottom: 10px;
        }

        .form-container button {
            display: block;
        }
</style>
