<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
const items = ref([
    {id:'0', label:'salchichas', purchased: false, priority: true}, 
    {id:'1', label:'gomitas', purchased: true,priority: false}, 
    {id:'2', label:'leche', purchased: true,priority: false},
    {id:'3', label:'refrescos', purchased: false,priority: true}
]);
const newItem = ref(''); 
const newItemHighPriority = ref(false);
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>

<!-- Agrupando en un div las entradas -->
<form class="add-item fomr" v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })">
    
    <!-- entrada de texto -->
    <input type="text" 
    placeholder="Agregar"  
    v-model.trim="newItem">
    
    <!-- Caja de seleccion de importancia-->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      importancia
    </label>
<!-- Boton -->

    <button 
    :disabled="newItem.length == 0"
    class="btn btn-primary">

    Guardar</button>
  
</form>
<!-- lista clase con objetos  -->
<ul>
    <li
         v-for="{label, id, purchased, priority} in items" 
         :key="id" 
         :class="{strikeout: purchased, priority: priority, }"
         class="amazing" > 
         {{priority ?"🎇": "🎃"}} {{label}} 
        </li>
  </ul>
  <!-- lista clase con arreglos  -->
  <ul>
    <li
         v-for="{label, id, purchased, priority} in items" 
         :key="id" 
         :class="[purchased ? 'strikeout': '', priority ? 'priority' : '']"> 
         {{priority ?"🎇": "🎃"}} {{label}} 
        </li>
  </ul>
  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>
  <p v-if="items.length === 0"> 🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>


<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>