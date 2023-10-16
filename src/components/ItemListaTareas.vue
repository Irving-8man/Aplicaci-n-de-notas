<script setup>

defineProps(['titulo', 'tarea', 'completado'])

</script>

<template>
  <div class="item-lista">
    <div>
      <div class="datosItem">
        <p><b>Título: </b> {{ titulo }}</p>
        <div class="datosTarea">
          <p><b>Nota: </b> {{ tarea }}</p>
        </div>
      </div>
      <div style="display: flex; flex-direction: row; justify-content: end;">
        <div class="botonesItem">
          <button type="button" @click="this.$emit('editar-tarea')" style="margin-right: 10px;" class="type3button">Editar</button>
          <button type="button" @click="this.$emit('eliminar-tarea')" class="type1button">Eliminar</button>
        </div>
      </div>

    </div>
  </div>
</template>



<style scoped>
.item-lista {
  max-width: 100%;
  box-shadow: 0 4px 8px rgba(255, 255, 255, 0.2);
  border-radius: 3px;
  margin: 30px;
  padding: 20px;
}

.item-lista+.item-lista {
  margin: 30px;
}

.item-lista p {
  color: rgb(255, 255, 255);
}

.datosTarea {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}
</style>
