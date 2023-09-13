<template>
    <ul>
        <li>
            articulo: {{ props.articulo}}
        </li>
        <li>
            cantidad: {{ props.cantidad }}
        </li>
        <li>
            valor: {{ props.valor }}
        </li>
    </ul>
    <h3>Total compra: {{ props.valor }}</h3>

</template>
<script lang="ts">
export default{
    data(props){
        return{
            props
        }
    },
    props:{
        articulo:String,
        cantidad:Number,
        valor:Number
    }
}
</script>