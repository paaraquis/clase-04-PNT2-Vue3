<script setup>
import { ref, computed } from "vue";

const EDAD_MAYOR = 18;
const FILTRO_TODOS = "todos";
const FILTRO_MENORES = "menores";

const personajes = ref([
  { id: 1, nombre: "Homero", edad: 39 },
  { id: 2, nombre: "Marge", edad: 36 },
  { id: 3, nombre: "Bart", edad: 10 },
  { id: 4, nombre: "Lisa", edad: 8 },
  { id: 5, nombre: "Maggie", edad: 1 }
]);

const nombre = ref("");
const edad = ref("");
const filtroActivo = ref(FILTRO_TODOS);
let proximoId = 6;

const esMenor = (personaje) => personaje.edad < EDAD_MAYOR;

const cantidadTotal = computed(() => personajes.value.length);

const personajesVisibles = computed(() =>
  filtroActivo.value === FILTRO_MENORES
    ? personajes.value.filter(esMenor)
    : personajes.value
);

const obtenerClase = (personaje) => (esMenor(personaje) ? "menor" : "adulto");

const obtenerTextoAnios = (años) => (años === 1 ? "año" : "años");

const agregarPersonaje = () => {
  const nombreLimpio = nombre.value.trim();
  const datosValidos = nombreLimpio !== "" && edad.value !== "";

  if (datosValidos) {
    const nuevoPersonaje = {
      id: proximoId,
      nombre: nombreLimpio,
      edad: edad.value
    };

    proximoId += 1;
    personajes.value.push(nuevoPersonaje);

    nombre.value = "";
    edad.value = "";
  }
};
</script>

<template>
  <h2>Personajes</h2>

  <label>Nombre: <input v-model="nombre" /></label>
  <label>Edad: <input v-model="edad" type="number" min="0" /></label>
  <button @click="agregarPersonaje">Agregar</button>

  <div>
    <button @click="filtroActivo = FILTRO_TODOS">Todos</button>
    <button @click="filtroActivo = FILTRO_MENORES">Menores</button>
  </div>

  <p>Cantidad: {{ cantidadTotal }}</p>

  <ul v-if="personajesVisibles.length > 0">
    <li
      v-for="personaje in personajesVisibles"
      :key="personaje.id"
      :class="obtenerClase(personaje)"
    >
      {{ personaje.nombre }} — {{ personaje.edad }}
      {{ obtenerTextoAnios(personaje.edad) }}
    </li>
  </ul>
  <p v-else>No hay personajes para mostrar.</p>
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