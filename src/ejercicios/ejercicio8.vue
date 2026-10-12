<script setup>
const EDAD_MAYOR = 18;

const personajes = [
  { id: 1, nombre: "Homero", edad: 39 },
  { id: 2, nombre: "Marge", edad: 36 },
  { id: 3, nombre: "Bart", edad: 10 },
  { id: 4, nombre: "Lisa", edad: 8 }
];
/*
function obtenerClase(edad) {
  return edad < EDAD_MAYOR ? "menor" : "adulto";
}*/
const obtenerClase = (edad) => (edad < EDAD_MAYOR ? "menor" : "adulto");

</script>

<template>
  <ul>
    <!--:class="personaje.edad < 18 ? 'menor' : 'adulto'"-->
    <li
      v-for="personaje in personajes"
      :key="personaje.id"
      :class="obtenerClase(personaje.edad)"
    >
      {{ personaje.nombre }} — {{ personaje.edad }} años
    </li>
  </ul>
</template>

<style scoped>
.menor {
    color: blue;
}
.adulto {
    color: black;
font-weight: bold;
}
</style>