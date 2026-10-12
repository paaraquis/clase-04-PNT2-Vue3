<script setup>
import { ref, computed } from "vue";

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

const menores = computed(() =>
  personajes.value.filter((personaje) => personaje.edad < EDAD_MAYOR)
);

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

  <h3>Personajes</h3>
  <ul>
    <li
      v-for="personaje in personajes"
      :key="personaje.id"
      :class="obtenerClase(personaje.edad)"
    >
      {{ personaje.nombre }} — {{ personaje.edad }} años
    </li>
  </ul>

  <h3>Personajes menores de edad</h3>
  <ul>
    <li v-for="personaje in menores" :key="personaje.id">
      {{ personaje.nombre }} — {{ personaje.edad }} años
    </li>
  </ul>
</template>

<style>
.menor {
  color: blue;
}

.adulto {
  color: black;
  font-weight: bold;
}
</style>