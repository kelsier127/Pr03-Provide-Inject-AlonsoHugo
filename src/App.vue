<script setup>
  import { ref } from 'vue'
  import SelectorDivisa from './components/SelectorDivisia.vue'

  let titulo = ref("")
</script>

<template>
  <div>
    <h1>{{ titulo }}</h1>
    <input type="text" v-model="titulo">
    <SelectorDivisa/>

  </div>
</template>

<style scoped>
div{
  display: grid;
  justify-content: center;
}

input{
  border-radius: 5px;
  border: 0.2px solid;
  margin: 10px;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
