<script setup>
//— Inputs sincronizados con v-model, nombre, edad
  import { ref } from 'vue'
  const nombre = ref('')
  const edad = ref(0)
</script>

<template>
    <input v-model="nombre" type="text" placeholder="Ingrese su nombre">
    <input v-model="edad" type="number" placeholder="Ingrese su edad">
  <p> Nombre: {{ nombre }}</p>
  <p> Edad: {{ edad }}</p>  
</template>

<style scoped></style>