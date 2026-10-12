<script setup>
    const personajes = [
    { id: 1, nombre: "Homero", edad: 39 },
    { id: 2, nombre: "Marge", edad: 36 },
    { id: 3, nombre: "Bart", edad: 10 },
    { id: 4, nombre: "Lisa", edad: 8 }
    ];
</script>

<template>
    <ul>
        <li v-for="personaje in personajes" :key="personaje.id">
            {{ personaje.nombre }} — {{ personaje.edad }} años
        </li>
    </ul>
</template>

<style scoped>

</style>