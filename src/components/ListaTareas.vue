<template>
  <div class="contenedorLista">
    <div>
      <!--Contendio de agragar notas-->
      <div class="contentAgregarTarea">
        <h3 style="text-align: center;">Agregar nueva nota</h3>
        <div class="content">
          <input type="text" v-model="tituloTarea" placeholder="Título">
          <textarea type="text" class="textAreaContenido" v-model="contenidoTarea" placeholder="Contenido"></textarea>
          <button @click="agregarTarea()"  class="type2button">Guardar nota</button>
        </div>
      </div>

      <!--Contenido de las notas-->
      <div class="contentListaTareas">
        <div>
          <h4 style="text-align: center;">Lista de Notas</h4>
          <div v-if="listaTareas.length === 0" style="margin-top: 20px;"> <p style="text-align: center; font-size: 17px;text-transform: uppercase;">No hay <span style=" text-decoration:line-through; color: rgb(250, 64, 64);">notas</span>...</p> </div>
          <div v-else>
            <ItemListaTareas v-for="(nota, index) in listaTareas" :key="index" :titulo="nota.tituloTarea" 
              :tarea="nota.contenidoTarea" @editar-tarea="editarNota(index)" @eliminar-tarea="eliminarTarea(index)">
            </ItemListaTareas>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-if="mostrarModalEdicion">
    <AvisoEditar :PtituloTareaEditada="tituloTareaEditada" :PcontenidoTareaEditada="contenidoTareaEditada"
      @cancelar-modal="cancelarEditar" 
      @guardar-modal="guardarEdicion"></AvisoEditar>
  </div>
</template>
  

<!--Forma de composition, orientado al ciclo de hooks-->
<script setup>
import { ref, reactive, toRefs } from 'vue';
import ItemListaTareas from './ItemListaTareas.vue';
import AvisoEditar from './AvisoEditar.vue';


//Para las notas
const listaTareas = reactive([{ tituloTarea: "Nota 1", contenidoTarea: "Mucha tarea" }])
const tituloTarea = ref('');
const contenidoTarea = ref('');

//Para edicion
const notaEnEdicion = reactive({});
const mostrarModalEdicion = ref(false);
const indexNota = ref(0)
const tituloTareaEditada = ref("");
const contenidoTareaEditada = ref("");

//Funcion para agregar tarea que contiene titulo y contenido
function agregarTarea() {
  if ((tituloTarea.value.trim() !== '') && (contenidoTarea.value.trim() !== '')) {
    listaTareas.push({ tituloTarea: tituloTarea.value, contenidoTarea: contenidoTarea.value });
    tituloTarea.value = '';
    contenidoTarea.value = '';
  }
}

//Función para eliminar la nota
function eliminarTarea(index) {
  listaTareas.splice(index, 1);
}

//Funcion para editar la nota
function editarNota(index) {
  indexNota.value = index;
  notaEnEdicion.value = listaTareas[index];
  tituloTareaEditada.value = notaEnEdicion.value.tituloTarea;
  contenidoTareaEditada.value = notaEnEdicion.value.contenidoTarea;
  mostrarModalEdicion.value = true;
}

//Fucion cancelar
function cancelarEditar() {
  notaEnEdicion.value = {}
  tituloTareaEditada.value = "";
  contenidoTareaEditada.value = "";
  indexNota.value = 0;
  mostrarModalEdicion.value = false;
}

//Funcion para gurdar los datos
function guardarEdicion(data) {
  console.log(data)
  let nuevaNota = { tituloTarea: data.tituloTareaE, contenidoTarea: data.contenidoTareaE};
  listaTareas[indexNota.value] = nuevaNota;
  cancelarEditar();
}

</script>



<style scoped>
.contenedorLista {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
}

.content {
  display: flex;
  flex-direction: column;
}

.textAreaContenido {
  margin: .625rem 0px;
  min-height: 5rem;
  min-width: 28.5rem;
  resize: none;
  font-size: 1rem;
}

.contentListaTareas {
  min-width: 100%;
}

.contentAgregarTarea {
  margin-bottom: 10vh;
}


</style>


