<script setup>
//Mostrar contenido según una condición
    import { ref, computed } from "vue";

    const edad = ref("");

    const claseEdad = computed(() => {
    let clase = "adulto";

    if (edad.value === "") {
        clase = "sin-edad";
    } else if (edad.value < 18) {
        clase = "menor";
    }

    return clase;
    });
</script>

<template>
  <input v-model="edad" type="number" placeholder="Ingrese su edad">

  <p :class="claseEdad"> Edad ingresada: {{ edad }}</p>
  
</template>

<style scoped>
    .sin-edad {
  background-color: lightgray;
  color: black;
}

.menor {
  background-color: lightblue;
  color: navy;
}

.adulto {
  background-color: green;
  color: white;
}
</style>