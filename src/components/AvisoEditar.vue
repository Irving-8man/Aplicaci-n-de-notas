<template>
    <div>
        <!-- Fondo del modal con fondo oscuro -->
        <div class="modal-background" @click="cancelarModal"></div>
        <div class="modal-content">
            <!-- Edición -->
            <div>
                <div class="contentAgregarTarea">
                    <h3 style="text-align: center;">Editar nota</h3>
                    <div class="content">
                        <input type="text" v-model="tituloTareaEditada" placeholder="Título">
                        <textarea type="text" class="textAreaContenido" v-model="contenidoTareaEditada"
                            placeholder="Contenido"></textarea>
                        <button @click="guardarModal" style="margin-bottom: 10px;" class="type2button">Guardar edición</button>
                        <button @click="cancelarModal" class="type1button">Cancelar edición</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';
const { PtituloTareaEditada, PcontenidoTareaEditada } = defineProps(['PtituloTareaEditada', 'PcontenidoTareaEditada'])
const emits = defineEmits(['cancelar-modal','guardar-modal']);

const activo = ref(true)
const tituloTareaEditada = ref(PtituloTareaEditada);
const contenidoTareaEditada = ref(PcontenidoTareaEditada);


function cancelarModal() {
    activo.value = false;
    emits('cancelar-modal');
}

function guardarModal() {
    activo.value = false;
    emits('guardar-modal',{tituloTareaE: tituloTareaEditada.value,contenidoTareaE:contenidoTareaEditada.value});
}

</script>

<style scoped>
/* Estilo para ocultar la casilla de verificación */
.hidden-checkbox {
    display: none;
}

.modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    z-index: 10;
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
}


.contentAgregarTarea {
    margin-bottom: 10vh;
}

input {
    margin-top: 20px;
    padding: 0;
    width: 28.5rem;
    height: 1.875rem;
    align-self: center;
    border-radius: 1px inherit;
}

.modal-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(71, 71, 71, 0.5);
    z-index: 999;
    cursor: pointer;
}

.modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #000000;
    padding: 20px;
    border-radius: 5px;
    text-align: center;
    box-shadow: 0 4px 8px rgba(255, 255, 255, 0.2);
    z-index: 1000;
}
</style>
