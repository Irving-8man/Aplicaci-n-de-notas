<template>
  <!--<div style="margin-top: 100px;">
    <input  v-model="text" placeholder="Ingresa un texto">
    <button @click="sumar()"> + </button>
    <button @click="resta()"> - </button>
    <div>
      <span>{{ lista }}</span>
      <span v-if="numero > 0">Número Positivo</span>
      <span v-else-if="numero < 0">Número Negativo</span>
      <span v-else>Cero</span>
    </div>
  </div>
-->
<!--
  <input type="text" v-model="tarea" @keyup.enter="agregarTarea()">
<button @click="agregarTarea()">Agregar Tarea</button>
<div v-if="lista.length === 0">No hay tareas</div>
<div v-else style="flex-direction: column;">
  <ItemListaTareas v-for="elem, index in lista" :key="index" 
  :tarea="elem.nombre" :completado="elem.completado"
  @marcar-tarea-completada="marcarTareaCompleta(elem)"
  @eliminar-tarea="eliminarTarea(index)"></ItemListaTareas>
</div>
-->
<ListaTareas class="lista"></ListaTareas>
</template>

<script setup>
import ItemListaTareas from './components/ItemListaTareas.vue'
import ListaTareas from './components/ListaTareas.vue';
import { ref, reactive } from 'vue';

let lista = reactive([{nombre: "Tarea 1", completado: false}, 
                      {nombre: 'Tarea 2', completado: true},
                      {nombre: 'Tarea 3', completado: false},
                      {nombre: 'Tarea 4', completado: false},
                    ])
let tarea = ref('')
//let numero = ref(1)

function agregarTarea(){
  if( tarea.value.trim() !== ''){
    lista.push({nombre: tarea.value, completado: false})
    tarea.value= ''
  }
}

function marcarTareaCompleta(elem){
  elem.completado = !elem.completado
}

function eliminarTarea(index) {
  lista.splice(index, 1);
}
//function resta() {numero.value--}
//function sumar() {lista.push('1')}
</script>

<style>
body {
  display: flex;
  justify-content: center;
  min-height: 100vh;
}

.lista {
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

h2 {
  text-align: center;
}

*,
*::before,
*::after {
  margin: 0;
  position: relative;
  font-weight: normal;
}

</style>
