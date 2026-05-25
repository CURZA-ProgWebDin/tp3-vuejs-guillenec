<script setup>
import TarjetaProductos from "./components/TarjetaProductos.vue";
import AppLayout from "./layouts/AppLayout.vue";
</script>

<template>
  <AppLayout>
    <p>
      Bienvenido a mi aplicación Vue. Aquí puedes encontrar información sobre
      nuestros productos y servicios.
    </p>
  </AppLayout>

  <TarjetaProductos>
    <template #header> Producto Destacado </template>
    <template #body>
      <p>Este es un producto increíble que no querrás perderte.</p>
    </template>
    <template #footer>
      <button>Comprar Ahora</button>
    </template>
  </TarjetaProductos>
</template>
