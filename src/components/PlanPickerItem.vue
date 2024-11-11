<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
         {{ name }} {{ selected ? '🧸' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//import ref function
import {ref} from 'vue';
//definir las props 
//defineprops(['name','planIcon)]']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }
});
//define un evento 
const emit= defineEmits(['select']);
//variable que permite recordar si el plan a sido seleccionado 
const selected = ref(false); 
//funcion que permite cambiar  el estado de la variable
//select
const selectPlan =() =>{
  selected.value=true;
  //emitir evento de que el 
  //plan ha sido seleccionado
  emit ('select', props.name);
};
</script>

<style scoped>
/* Estilos */
</style>
