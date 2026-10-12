//Crear un contador inicializado en 0 utilizando ref.

<script setup>
  import { ref } from 'vue'
  const contador = ref(0)
</script>

<template>
  <h1>
    Contador: {{ contador }}
  </h1>
  <p>
    <button @click="contador--">Restar</button>
    <button @click="contador = 0">Resetear</button>
    <button @click="contador++">Sumar</button>
  </p>
</template>

<style scoped></style>