<template>
  <div>
    <h2>Lista de Profesionales</h2>
    <p v-if="lista.length === 0">Cargando lista...</p>
    <ul v-else>
      <li v-for="profesion in lista" :key="profesion.id">
        <strong>{{ profesion.nombre }}</strong>: {{ profesion.descripcion }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import profesiones from "../resources/profesionales";

const lista = ref([]);

onMounted(() => {
  setTimeout(() => {
    lista.value = profesiones;
  }, 3000);
});
</script>
