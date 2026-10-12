<script setup>
import { ref } from "vue";

const EDAD_MAYOR = 18;

const personajes = ref([
  { id: 1, nombre: "Homero", edad: 39 },
  { id: 2, nombre: "Marge", edad: 36 },
  { id: 3, nombre: "Bart", edad: 10 },
  { id: 4, nombre: "Lisa", edad: 8 }
]);

const nombre = ref("");
const edad = ref("");
let proximoId = 5;

const obtenerClase = (edadPersonaje) =>
  edadPersonaje < EDAD_MAYOR ? "menor" : "adulto";

const agregarPersonaje = () => {
  const nombreLimpio = nombre.value.trim();
  const datosValidos = nombreLimpio !== "" && edad.value !== "";

  if (datosValidos) {
    personajes.value.push({
      id: proximoId++,
      nombre: nombreLimpio,
      edad: edad.value
    });

    nombre.value = "";
    edad.value = "";
  }
};

</script>

<template>
  <label>Nombre: <input v-model="nombre" /></label>
  <label>Edad: <input v-model="edad" type="number" min="0" /></label>
  <button @click="agregarPersonaje">Agregar</button>

  <ul>
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