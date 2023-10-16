<!--Este componente se encarga de estar montando y desmontarlos-->

<script setup>
import ListaTareas from './components/ListaTareas.vue';
</script>

<template>
  <div class="header">
    <h1 class="header-titulo">Aplicación de Notas</h1>
  </div>
  <ListaTareas></ListaTareas>
</template>



<style>
:root {
  --tipografiaTitulo: 'Times New Roman', Times, serif;
  --tipografiaTexto: Arial, Helvetica, sans-serif;
}

body {
  min-height: 100vh;
  min-width: 100%;
  font-family: var(--tipografiaTitulo);
  background-color: rgb(27, 26, 26);
  font-size: 1.25rem;
  color: white;
  overflow-x: hidden;
}

.header {
  border-bottom: 2px dashed white;
  padding-top: 10vh;
  margin-bottom: 10vh;
}

.header-titulo {
  color: white;
  font-size: larger;
  font-size: 3.125rem;
}

button {
  background-color: #000000;
  color: rgb(255, 255, 255);
  border: 1px dashed white;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 14px;
  font-weight: 530;
}

.type1button:hover {
  border-color: rgb(255, 0, 0);
  color: rgb(230, 102, 102);
}

.type2button:hover {
  border-color: #00ff08;
  color: #6ce770;
}

.type3button:hover {
  border-color: #FFD700;
  color: #ebd976;
}

input {
  margin-top: 20px;
  padding: 0;
  width: 28.5rem;
  height: 1.875rem;
  align-self: center;
  border-radius: 1px inherit;
  font-size: 1rem;
  font-weight:600;
}

*,
*::before,
*::after {
  margin: 0;
}</style>
