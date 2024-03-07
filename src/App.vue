<script setup>
// Importando funcion para crear referencias reactivas
import { ref } from 'vue'
//Creando un tipo de referencia reactiva de tipo string
const header = ref('App Lista de Compras');
const shoppingIcon = ref ('material-icons shopping-cart-icon');
//Creando una referencia reactiva para almacenar el valor de la lista
const items = ref([
{id: 0, label: 'Arroz'}, 
{id: 1, label: 'Avena'}, 
{id: 2, label: 'Arandanos'}, 
{id: 3, label: 'Nuez'}, 
{id: 4, label: 'Almendras'}
]);
const newItem = ref('');
const newItemPriority = ref('low')
</script>

<template>
  <h1><i :class="shoppingIcon">local_mall</i> {{ header }}</h1>
  <input v-model="newItem" type="text" placeholder="Agregar Articulo">
  <!-- Radio Buttons -->
  <label><input type="radio" v-model="newItemPriority" value="low">Baja</label>
  <label><input type="radio" v-model="newItemPriority" value="high">Alta</label>
  {{ newItemPriority === 'low'?'🧊':'🔥' }}
  <ul>
  <li v-for="({ id, label }, i) in items" v-bind:key="id">⭐ {{ label }}</li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>