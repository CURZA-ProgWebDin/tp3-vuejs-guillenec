<script setup>
import { onActivated, onDeactivated, onMounted, onUnmounted } from "vue";
import { productos } from "../../data/productos.js";
import ListaProductos from "../ListaProductos.vue";

onMounted(() => console.log("TabTodos - montado"));
onUnmounted(() => console.log("TabTodos - desmontado"));
onActivated(() => console.log("TabTodos - activado"));
onDeactivated(() => console.log("TabTodos - desactivado"));
</script>

<template>
  <section>
    <h2>Todos</h2>
    <ListaProductos :productos="productos" />
  </section>
</template>
