<script setup>
import { ref, computed } from "vue";
// Modelo
const header = ref('App lista de compras');
//---items---
//items model
const items = ref([
  {id:'0', label: '10 bolillos',purchased:false,priority:true},
  {id:'1', label: '1 crema de litro',purchased:true,priority:true},
  {id:'2', label: '1/4 de jamon',purchased:false,priority:false},
  {id:'3', label: '1 nutella',purchased:true,priority:false},
]);
//item-metodo
const seveItem = () => {
  //accediendo a la variable reactiva items value.
  items.value.push({id:items.value.length + 1, label: newItem.value,
    //---Funcionamiento de items de alta prioridad--
    highPriority: newItemHighPriority.value
  });
  //limpia el imput (la entrada de texto) 
  newItem.value='';
  //---Funcionamiento de items de alta prioridad--
  newItemHighPriority.value = false;
};
//---formulario--
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);
const activateEdition = (activate)=>{
  editing.value=activate;
  //---Funcionamiento de items de alta prioridad--
  newItemHighPriority.value = false;
};
// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};
// Creando una propiedad computada
const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
});
// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse(); 
  
});
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

  
   <!---para poder poner link enla caja de texto v-bind:href="newItem"
     para que cuando este bacia la caja de texto tenga un link
     :href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" 
    target="_blank" -->
 <!---colocando un iperenlace
  <a 
    :href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" 
    target="_blank">
    {{ newItem === '' ? '😒 Link' : newItem }}
  </a>
  -->
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
  
  <!--Desabilitando el boton cuando esta bacia la caja de texto
         :disabled="newItem.length==0"-->
  <button
  :disabled="newItem.length==0" 
  class="btn btn-primary">
    Salvar Articulo
  </button>
  	<!-- Contador -->
    <p class="counter">
    {{ characterCount }} / 200
  </p>
  </form>
  <ul></ul>

  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  
  <!-- Lista -->
   <!-- desestructuracion -->
  <!-- desestructurando index 
    v-for="({ id, label, purchased, priority }, index) 
    o referencia al objeto directamente   item -->
<!-- Lista    -->
<ul>
  <li 
	v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
  :class="{ strikeout: purchased, priority: highPriority }" 
	@click="togglePurchased(reversedItems[index])" 
  v-bind:key="id">
	  ➡️ {{ label }}
</li>
  </ul>
  <p v-if="items.length === 0">🥀 No hay elementos en la lista</p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>