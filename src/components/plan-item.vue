<template>
  <div class="plan">
    <div class="description">
      <span class="title">
         {{ name }} 
      </span>
    </div>
  </div>
</template>

<script setup>
//definir las props 
//defineprops(['name','planIcon)]']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
/* Estilos */
</style>
