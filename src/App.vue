<script setup>
import { ref } from 'vue';

const header = ref('App Lista de compras');
const items = ref([
  // {id: 1, label: '10 bolillos'},
  // {id: 2, label: '1 lata de frijoles'},
  // {id: 3, label: '2 lata de atún'}
]);
// Agregando nuevos elementos
const saveItem = () =>  {
  items.value.push({id: items.value.length + 1, label: newItem.value})
  // limpiando el contenido de item
  newItem.value = "";
};
const newItem = ref('');
const newItemHighPriority = ref (false);
</script>

<template>
  <div class="header"> 
    <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
    <button class="btn">Cancelar</button>
    <button class="btn btn-primary">Agregar Articulo</button>
  </div>
 <form v-on:submit.prevent = "saveItem" class="add-item form">
<!-- input de nuevo articulo -->
  <input  v-model.trim="newItem" type="text" placeholder="Ingresar nuevo articulo">
  <!-- Check Boxes -->
  <label>
    <input v-model="newItemHighPriority" 
    type="checkbox">
    Alta Prioridad
  </label>
  {{ newItemHighPriority ? "🔥" : "🧊" }}
  <!-- Boton de UI -->
  <button class="btn btn-primary">Salvar Articulo</button>
</form>
  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">
      🔹 {{ label }}
    </li>
  </ul>
  <p v-if="items.length === 0" > 🥀 Lista de compras vacía</p>
  <p v-else>🔥 Ingrese mas items 🔥</p>
</template>


<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
