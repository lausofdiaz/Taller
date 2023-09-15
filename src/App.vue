<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import ComponentsTaller from './components/ComponentsTaller.vue'
import ViewsTaller from './views/ViewsTaller.vue'

</script>

<template>
  <main>
    <section class="vista">
      <ViewsTaller></ViewsTaller>
    </section>
  </main>
</template>

<style> 
*{
  margin: 0;
  padding: 0;

}
.vista{
    display: grid;
    grid-template-areas: "formulario componente" ;
    grid-template-columns: 1fr 1fr;
    width: 100vw;
    height: 100vh;
}

</style>