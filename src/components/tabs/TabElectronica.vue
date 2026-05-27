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

const productosElectronica = computed(() =>
  productos.filter((p) => p.categoria === "Electrónica"),
);

onMounted(() => console.log("TabElectronica - montado"));
onUnmounted(() => console.log("TabElectronica - desmontado"));
onActivated(() => console.log("TabElectronica - activado"));
onDeactivated(() => console.log("TabElectronica - desactivado"));
</script>

<template>
  <section>
    <h2>Electrónica</h2>
    <ListaProductos :productos="productosElectronica" />
  </section>
</template>
