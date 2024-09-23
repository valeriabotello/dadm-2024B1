<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
const items = ref([
{id:'0', label: '10 bolillos'},
{id:'1',label: 'lata frijoles'},
{id:'2',label: 'refrescos'},
{id:'3',label: 'chetos'},
{id:'4',label: 'paletas'}
]);
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
    </h1>
   <ul>
   <li v-for="item in items" :key="item.id"> 🛒 {{item.label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>