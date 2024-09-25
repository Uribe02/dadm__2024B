<script setup>
import{ref}from'vue';
const header = ref ('app lista de compras');
const items = ref([
    {id:'0',label:'2 chetos Bolitas de queso'},
    {id:'1',label:'1 bolsa nues'},
    {id:'2',label:'3 palomitas'},
    {id:'3',label:'1 nutella'},
    

]);
</script>

<template>

<h1>
    <i class="material-icons">local_mall</i>
    {{ header }}
</h1>
<ul>
    
<li v-for="item in items" :key="item.id">➡️ {{ item.label }}</li>
</ul>
</template>

<style scoped>
.shopping-cart-icon{ 
    font-size:2rem ;
}
</style>
