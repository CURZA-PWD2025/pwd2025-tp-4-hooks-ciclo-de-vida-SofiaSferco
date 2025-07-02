<template>
  <div>
    <h2>Lista de Tareas</h2>
    <input v-model="nuevaTarea" placeholder="Nueva tarea" />
    <button @click="agregarTarea">Agregar</button>
    <ul>
      <li
        v-for="(tarea, index) in tareas"
        :key="index"
        :style="{ color: tareasPrevias.includes(tarea) ? 'blue' : 'black' }"
      >
        {{ tarea }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from "vue";

const tareas = ref(["Comprar pan", "Lavar ropa", "Estudiar"]);
const tareasPrevias = ref([...tareas.value]);
const nuevaTarea = ref("");

onBeforeUpdate(() => {
  console.log("Lista aún no modificada");
});

onUpdated(() => {
  console.log("Lista modificada");
  tareasPrevias.value = [...tareas.value];
});

function agregarTarea() {
  if (nuevaTarea.value.trim() !== "") {
    tareas.value.push(nuevaTarea.value.trim());
    nuevaTarea.value = "";
  }
}
</script>
