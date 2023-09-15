<script setup lang="ts">
import {ref,defineProps, defineEmits} from 'vue';

const props = defineProps({
  articulos:Array
});

const emit = defineEmits(['borrar'])

function eliminar(index){
emit('borrar',index)
}
</script>

<template>
    <table class="tabla">
        <thead>
          <tr>
            <th  >#</th>
            <th  >Artículo</th>
            <th  >Cantidad</th>
            <th  >Valor unitario</th>
            <th  >Total</th>
            <th  >Borrar</th>
          </tr>
        </thead>
        <tbody >
          <tr  v-for="(i,index) of props.articulos">
            <td >{{ index+1 }}</td>
            <td>{{ i.articulo }}</td>
            <td >{{ i.cantidad }}</td>
            <td >{{ i.valor }}</td>
            <td >{{ i.valor * i.cantidad }}</td>
            <td>
            <button @click="eliminar(index)">Borrar</button>
            </td>
          </tr>
        </tbody>
      </table>
      <h3>Valor total: </h3>
</template>
<style scoped>
table{
  text-align: left;
  width: 400px;
  border-collapse: collapse;
}
th, td{
  padding: 10px;
}

thead{
  background-color: #ddd;
}
</style>