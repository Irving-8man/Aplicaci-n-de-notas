<template>
  <div class="item-lista">
    <input type="checkbox" :checked="completado" 
    @change="this.$emit('marcar-tarea-completada')">
    <span :class="{ completado: completado }">{{ tarea }}</span>
    <button @click="this.$emit('eliminarTarea')">Eliminar</button>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps(['tarea', 'completado'])

</script>

<style scoped>
.completado {
  text-decoration: line-through;
}

.item-lista{
    display: flex;
    align-items: center;
    height: 5vh;
    margin-top: 0;
}

span {
    margin: 5px 8px;
    
}

button{
    position: absolute;
    right: 0;
}
</style>
