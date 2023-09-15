<script setup lang="ts">
import {ref,defineProps, defineEmits,computed} from 'vue';

const props = defineProps({
  articulos:Array
});
const emit = defineEmits(['borrar'])
function eliminar(index){
emit('borrar',index)
}

const valorTotal = computed(()=>{
  let suma = 0
  props.articulos?.forEach((elemento)=>{
    suma += elemento.cantidad*elemento.valor
  })
  return suma
})

const porcentaje = computed (()=>{
let descuentoCantidad = 0
let descuentoPorcentaje = 0
let mayor = 0

if (props.articulos?.length>=12){
descuentoCantidad=0.2;
} else if (props.articulos?.length>=6){
descuentoCantidad=0.1;
}else {
  descuentoCantidad=0;
}

if(valorTotal.value >=240000){
    descuentoPorcentaje = 0.15;
  } else if (valorTotal.value >=120000){
    descuentoPorcentaje = 0.1;
  } else if(valorTotal.value >= 60000){
    descuentoPorcentaje = 0.05;
  }else{
    descuentoPorcentaje=0;
  }

if (descuentoCantidad>descuentoPorcentaje){
mayor = descuentoCantidad
} else {
mayor = descuentoPorcentaje
}

let totalConDescuento = valorTotal.value*mayor
  return totalConDescuento

})


const totalApagar = computed(()=>{
let totaltotal = valorTotal.value - porcentaje.value
return totaltotal
})
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
      <h3>Valor total: ${{ valorTotal }} </h3>
      <h3>Descuento: {{ porcentaje }}% </h3>
      <h3>Total a pagar: ${{ totalApagar }} </h3>
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