<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref} from 'vue';
//creando una referencia reactiva 
//para almacenar el plan seleccionado
const selectedPlan=ref(null);

const plans
 = ref (['El cafetero','Él lechero','El Intelectual']);
 const selectPlan=(name)=>{
    //almacenar el plan seleccionado 
    selectedPlan.value=name
 };
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
    <p>{{ selectedPlan }}</p>
</template>



<style  scoped>

</style>