<template>
  <div>
    <h1>Trabajo Práctico N°4 - Ciclo de Vida de Componentes</h1>
    <div style="margin-bottom: 1rem;">
      <button @click="componenteSeleccionado = 'Lista'">Lista</button>
      <button @click="componenteSeleccionado = 'Tareas'">Tareas</button>
      <button @click="componenteSeleccionado = 'DimensionComponente'">Dimensiones</button>
      <button @click="componenteSeleccionado = 'Alertas'">Alertas</button>
    </div>

    <component :is="componentes[componenteSeleccionado]" />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Lista from "./components/Lista.vue";
import Tareas from "./components/Tareas.vue";
import DimensionComponente from "./components/DimensionComponente.vue";
import Alertas from "./components/Alertas.vue";

const componentes = {
  Lista,
  Tareas,
  DimensionComponente,
  Alertas,
};

const componenteSeleccionado = ref("Lista");
</script>
