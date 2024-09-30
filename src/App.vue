<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
const items = ref([
    {id:'0', label: 'salchichas'}, 
    {id:'1', label: 'gomitas'}, 
    {id:'2', label: 'leche'},
    {id:'3', label: 'refrescos'}
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
    <button class="btn btn-primary">
    Guardar</button>
  
</form>
    
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🔥':'🛍️'}} {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>