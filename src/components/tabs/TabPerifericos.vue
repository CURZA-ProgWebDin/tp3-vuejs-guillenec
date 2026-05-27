<script setup>
import {
  computed,
  onActivated,
  onDeactivated,
  onMounted,
  onUnmounted,
} from "vue";
import { productos } from "../../data/productos.js";
import ListaProductos from "../ListaProductos.vue";

const productosPerifericos = computed(() =>
  productos.filter((p) => p.categoria === "Periféricos"),
);

onMounted(() => console.log("TabPerifericos - montado"));
onUnmounted(() => console.log("TabPerifericos - desmontado"));
onActivated(() => console.log("TabPerifericos - activado"));
onDeactivated(() => console.log("TabPerifericos - desactivado"));
</script>

<template>
  <section>
    <h2>Periféricos</h2>
    <ListaProductos :productos="productosPerifericos" />
  </section>
</template>
