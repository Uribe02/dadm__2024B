<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');
//---items---
//items model
const items = ref([
  {id:'0', label: '10 bolillos'},
  {id:'1', label: '1 crema de litro'},
  {id:'2', label: '1/4 de jamon'},
  {id:'3', label: '1 nutella'}
]);
//item-metodo
const seveItem = () => {
  //accediendo a la variable reactiva items value.
  items.value.push({id:items.value.length + 1, label: newItem.value});
  //limpia el imput 
  newItem.value='';
};
//---formulario--
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);
const activateEdition = (activate)=>{
  editing.value=activate;
};


//metodos 
</script>

<template>
  
<div class="header">
  <h1>
   <i class="material-icons shopping-cart-icon">local_mall</i> 
    {{ header }} 
  </h1>
  <button
   v-if="editing" 
   class="btn"
    @click="activateEdition(false)">
    Cancelar
  </button>
  <button
   v-else
    class="btn btn-primary" 
    @click="activateEdition(true)">
    Agregar Articulo
  </button>
  </div>

  <!---colocando un iperenlace-->
   <!---para poder poner link enla caja de texto v-bind:href="newItem"-->
     <!--para que cuando este bacia la caja de texto tenga un link
     :href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" 
    target="_blank" -->
 
  <a 
    :href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" 
    target="_blank">
    {{ newItem === '' ? '😒 Link' : newItem }}
  </a>
  <!--- agrupando entradas de usuario-->
  <form 
  class="add-item form"
  v-if="editing"
   v-on:submit.prevent="seveItem">
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad
  </label>
  <!--Boton-->
  <button class="btn btn-primary">
    Salvar Articulo
  </button>
  </form>
  <ul></ul>

  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id"> 🛍 {{  item.label }} </li>
  </ul>
  <p V-if="items.length === 0">🥀NO HAY ELEMNTOS EN LISTA🥀 </p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>