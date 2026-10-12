<script setup>
//Mostrar contenido según una condición
  import { ref } from 'vue'

  const nombre = ref("");
  const edad = ref("");
</script>

<template>
    <input v-model="nombre" type="text" placeholder="Ingrese su nombre">
    <input v-model="edad" type="number" placeholder="Ingrese su edad">
  <p> Nombre: {{ nombre }}</p>
  <p> Edad: {{ edad }}</p>  
  <p v-if="edad === ''"></p>
  <p v-else-if="edad < 18">Es menor de edad</p>
  <p v-else>Es mayor de edad</p>
</template>

<style scoped>

</style>

