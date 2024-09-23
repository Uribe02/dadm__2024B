<script setup>
import{ref}from'vue';
const header = ref ('app lista de compras');

</script>

<template>

<h1>
    <i class="material-icons">local_mall</i>
    {{ header }}
    </h1>
</template>

<style scoped>
.shopping-cart-icon{
    font-size:2rem ;
}
</style>
