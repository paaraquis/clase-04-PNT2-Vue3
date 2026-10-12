<script setup>
//— Cambiar una clase dinámicamente con v-bind
  import { ref } from 'vue'

  const activo = ref(false);
</script>

<template>
    <button @click="activo = !activo">Cambiar estado</button>

    <p :class="activo ? 'activo' : 'inactivo'">
    Estado actual: {{ activo ? "Activo" : "Inactivo" }}
    </p>
</template>

<style scoped>
.activo {
    background-color: green;
    color: white;
}
.inactivo {
    background-color: lightgray;
    color: black;
}
</style>