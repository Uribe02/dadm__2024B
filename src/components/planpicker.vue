<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref, onMounted, onUnmounted} from 'vue';

//creando una referencia reactiva 
//para almacenar el plan seleccionado
const selectedPlan=ref(null);

const plans
 = ref (['El cafetero','Él lechero','El Intelectual']);
 const selectPlan=(name)=>{
    //almacenar el plan seleccionado 
    selectedPlan.value=name
 };

 const plansWrapper = ref (null);

 //intentando obtener la rferencia al elemento .plans 

 console.log("termina de ejecutar el scrip setup 🧸");

//registrando el hook mounted
onMounted(() =>{
console.log("el componente planPiker de ha montado 🎉");
console.log(plansWrapper.value);
});

//registrando el hook mounted
onUnmounted(() =>{
console.log("el componente planPiker de ha desmontado 😐");
});
</script>


<template>
    <div ref="plansWrapper" class="plans">    
<PlanPickerItem
 v-for="plan in plans"
 :key="plan"
  :name="plan"
  @select="selectPlan"
  :select-plan="selectedPlan"
  />
    </div>

</template>



<style  scoped>

</style>