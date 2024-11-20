<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref, onMounted} from 'vue';
//creando una referencia reactiva 
//para almacenar el plan seleccionado
const selectedPlan=ref(null);

const plans
 = ref (['El cafetero','Él lechero','El Intelectual']);
 const selectPlan=(name)=>{
    //almacenar el plan seleccionado 
    selectedPlan.value=name
 };
 //intentando obtener la rferencia al elemento .plans 

 console.log("termina de ejecutar el scrip setup 🧸");

//registrando el hoo mounted
onMounted(() =>{
console.log("el componente planPiker de ha montado 🎉");
console.log(document.querySelector('plans'));
});
</script>


<template>
    <div class="plans">    
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