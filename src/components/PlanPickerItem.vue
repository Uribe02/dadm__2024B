<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
         {{ name }} {{ isSelected ? '🧸' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//importando la funcion para crear
//propiedad computada
import { computed } from 'vue';
//definir las props 
//defineprops(['name','planIcon)]']);
const props = defineProps({
  //esquema
  name: {
    type: String,
    required: true
  },
  //definicion sencilla
  selectPlan:String
});
//define un evento 
const emit= defineEmits(['select']);

//funcion que permite cambiar  el estado de la variable
//select
const selectPlan =() =>{
  //emitir evento de que el 
  //plan ha sido seleccionado
  emit ('select', props.name);
};

// creando una propiedad computada 
//para saber si el plan ha sido seleccionado 
const isSelected = computed(()=>{
  return props.name === props.selectPlan;
})


</script>

<style scoped>
/* Estilos */
</style>
