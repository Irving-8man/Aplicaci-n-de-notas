<template>
  <div class="contenedorLista">
    <h2>Lista de Tareas</h2>
    <input v-model="nuevaTarea" @keyup.enter="addtarea()" 
    placeholder="Nueva Tarea">
    <div v-if="listaTareas.length === 0"  style="display: 
    flex; justify-content: center;">No hay tareas</div>
    <div v-else>
      <ItemListaTareas v-for="(tarea, index) in listaTareas" :key="index" 
      :tarea="tarea.nombre"
        :completado="tarea.completado" 
        @marcar-tarea-completada="marcarTareaCompletada(index)"
        @eliminar-tarea="eliminarTarea(index)"></ItemListaTareas>
    </div>
  </div>
</template>
  

<script setup>
import ItemListaTareas from './ItemListaTareas.vue';
import { ref, reactive } from 'vue';

const listaTareas = reactive([{nombre: "Tarea 1", completado: false}, 
                      {nombre: 'Tarea 2', completado: true},
                      {nombre: 'Tarea 3', completado: false},
                      {nombre: 'Tarea 4', completado: false},
                    ])
const nuevaTarea = ref('')

function addtarea() {
  if (nuevaTarea.value.trim() !== '') {
    listaTareas.push({ text: nuevaTarea.value, completed: false });
    nuevaTarea.value = '';
  }
}

function marcarTareaCompletada(index) {
  listaTareas[index].completed = !this.listaTareas[index].completed;
}

function eliminarTarea(index) {
  listaTareas.value.splice(index, 1);
}
</script>

<style scoped>
div {
  margin-top: 15px;
  min-width: 30vw;
  max-width: 30vw;
}

.contenedorLista{
  margin-top: 20vh;
}

input {
  margin: 15px 0px 0px 0px;
  padding: 0;
  align-self: center;
}
</style>