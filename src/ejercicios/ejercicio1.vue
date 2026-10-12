<script setup>
    const personaje = {
      nombre: "Lisa",
      edad: 8,
      rol: "Hija"
    };
</script>

<template>
  <h1>
    {{ personaje.nombre }}  
  </h1>
  <p>
    Edad: {{ personaje.edad }}
  </p>
  <p>
    Rol: {{ personaje.rol }}
  </p>
</template>

<style scoped></style>