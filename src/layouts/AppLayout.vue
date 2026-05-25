<script setup>
import BaseLayout from "./BaseLayout.vue";
</script>

<template>
  <BaseLayout>
    <template #header>
      <h1>Mi Aplicación Vue</h1>
    </template>
    <template #main>
      <slot></slot>
      <h2>pruebas 123 Main</h2>
    </template>
    <template #footer>
      <h2>footer 123</h2>
    </template>
  </BaseLayout>
</template>
