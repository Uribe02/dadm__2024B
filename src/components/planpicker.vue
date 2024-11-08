<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref} from 'vue';
const plans
 = ref (['El cafetero','Él lechero','El Intelectual']);
</script>


<template>
    <div class="plans">    
<PlanPickerItem v-for="plan in plans" :key="plan" :name="plan" />
    </div>
</template>



<style  scoped>

</style>