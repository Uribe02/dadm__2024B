<template>
  <div class="header">
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activateEdition(false)">Cancelar</button>
    <button v-else class="btn btn-primary" @click="activateEdition(true)">Agregar Artículo</button>
  </div>

  <!-- Formulario para agregar artículos -->
  <form class="add-item form" v-if="editing" @submit.prevent="seveItem">
    <input v-model="newItem" type="text" placeholder="Agregar un artículo" />
    <!-- Checkbox para seleccionar prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta Prioridad
    </label>
    <!-- Botón para guardar -->
    <button :disabled="newItem.length == 0" class="btn btn-primary">Salvar Artículo</button>
  </form>

  <!-- Lista de artículos -->
  <ul>
    <li
      v-for="({ id, label, purchased, priority }, index) in items"
      :key="id"
      :class="{ strikeout: purchased, priority: priority }"
      @click="togglePurchased(items[index])"
    >
      {{ priority ? "🔥" : "💧" }} {{ label }}
    </li>
  </ul>

  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<script setup>
import { ref } from 'vue';

// Variables reactivas
const header = ref('App lista de compras');
const items = ref([
  { id: '0', label: '10 bolillos', purchased: false, priority: true },
  { id: '1', label: '1 crema de litro', purchased: true, priority: true },
  { id: '2', label: '1/4 de jamón', purchased: false, priority: false },
  { id: '3', label: '1 Nutella', purchased: true, priority: false },
]);

const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);

// Función para alternar el estado `purchased`
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

// Función para agregar un nuevo artículo
const seveItem = () => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    purchased: false,
    priority: newItemHighPriority.value,
  });
  newItem.value = '';
};

// Función para activar/desactivar edición
const activateEdition = (activate) => {
  editing.value = activate;
};
</script>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
.strikeout {
  text-decoration: line-through;
}
.priority {
  color: red;
}
</style>
