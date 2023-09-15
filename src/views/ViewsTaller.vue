
<script setup lang="ts">
import {ref} from 'vue';
import ComponenstTaller from '../components/ComponentsTaller.vue';
const articulo = ref('');
const cantidad= ref(1);
const valor= ref(1);
const articulos = ref([]);

function agregar(){
    const nuevoArticulo = {
    articulo: articulo.value,
    cantidad: cantidad.value,
    valor: valor.value
  };

  articulos.value.push(nuevoArticulo);

  articulo.value = '';
  cantidad.value = 1;
  valor.value = 1;
}

function borrar(index){
    articulos.value.splice(index,1);
}
</script>


<template>   

        <form class="formulario">
            <div>
                <h2 class="titulo">Datos del Artículo</h2>
            <div class="campo">
                <label for="nombre">Nombre del Artículo:</label>
                <input type="text" v-model="articulo" placeholder="Nombre del artículo">
            </div>
            <div class="campo">
                <label >Cantidad de Artículos:</label>
                <input type="number"
               v-model="cantidad" placeholder="Cantidad" >
            </div>
            <div class="campo">
                <label >Valor del Artículo:</label>
                <input  v-model="valor"  type="number" placeholder="Valor" >
            </div>
            <button @click="agregar()" type="button" class="boton-agregar">Agregar</button>
            </div>
        </form>
        <section class="componente">
            <ComponenstTaller :articulos="articulos" @borrar="borrar"></ComponenstTaller>
        </section>
     

  </template>

<style scoped>
     
 
.componente{
  grid-area: componente;
}
        .formulario {
            grid-area: formulario;
            border: 1px solid #ccc;
            padding: 20px;
            max-width: 400px;
            display: flex;
            justify-content: center;
            height: 300px;
        }

        .titulo {
            font-size: 20px;
            margin-bottom: 10px;
        }

        .campo {
            margin-bottom: 15px;
        }

        .campo label {
            display: block;
            font-weight: bold;
        }

        .campo input {
            width: 250px;
            padding: 5px;

        }

        .boton-agregar {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
        }

        .boton-agregar:hover {
            background-color: #0056b3;
        }

</style>
