<script setup>
    import { ref } from 'vue'
</script>

<template>
    <div>
        <select v-model="moneda">
          <option value="$">Dolares ($)</option>
          <option value="€">Euros (€)</option>
        </select>
        <p>Moneda seleccionada: {{ moneda }}</p>
    </div>
</template>

<style scoped>

</style>