<script setup>
    import { provide, ref } from 'vue'
    import LlistaProductos from './ListaProductos.vue'

    let pepin="hola"

    let moneda = ref("$")

    provide("monedaId",moneda) 
</script>

<template>
    <div>
        
        <select v-model="moneda">
          <option value="$">Dolares ($)</option>
          <option value="€">Euros (€)</option>
        </select>
        <!--<p>Moneda seleccionada: {{ moneda }}</p>-->

        <LlistaProductos/>

    </div>
</template>

<style scoped>

</style>