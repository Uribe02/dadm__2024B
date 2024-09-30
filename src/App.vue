<script setup>
import{ref}from'vue';
const header = ref ('app lista de compras');
const items = ref([
    {id:'0',label:'2 chetos Bolitas de queso'},
    {id:'1',label:'1 bolsa nues'},
    {id:'2',label:'3 palomitas'},
    {id:'3',label:'1 nutella'},
    

]);
const newItem = ref('');
const newItemPriority=ref('low');

</script>

<template>

<h1>
    <i class="material-icons">local_mall</i>
    {{ header }}
</h1>
<input v-model.lazy="newItem" type="tex"
 placeholder="Agregar articulo">
 <!-- Radio de botones-->
  <label>
    <input type="radio" value="low" v-model="newItemPriority">
    Baja
</label>
  <label>
    <input type="radio" value="high" v-model="newItemPriority">
    Alta
</label>
{{ newItemPriority =='low'?'🦤':'🧸'}}
  <!-- Helados -->
  <label>
		<input type="checkbox" v-model="iceCreamFlavors" value="vanilla">
		Vanilla
	</label>
  <label>
		<input type="checkbox" v-model="iceCreamFlavors" value="chocolate">
		Chocolate
	</label>
  <label>
		<input type="checkbox" v-model="iceCreamFlavors" value="strawnerry">
		Strawberry
	</label>
<ul>
    
<li v-for="item in items" :key="item.id">➡️ {{ item.label }}</li>
</ul>
</template>

<style scoped>
.shopping-cart-icon{ 
    font-size:2rem ;
}
</style>
