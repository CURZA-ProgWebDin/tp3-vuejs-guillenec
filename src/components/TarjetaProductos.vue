<script setup>
import { ref } from "vue";

//Estado para saber qué producto está expandido
const productoExpandidoId = ref(null);

const toggleExpandido = (id) => {
  productoExpandidoId.value = productoExpandidoId.value === id ? null : id;
};
</script>

<template>
  <article class="tarjeta">
    <slot name="header">
      <span>Sin acciones disponibles</span>
    </slot>
    <section class="body">
      <slot
        name="body"
        :producto="producto"
        :expandida="productoExpandidoId == producto?.id"
        :toggleExpandido="() => toggleExpandido(producto?.id)"
      >
        <span>Sin acciones disponibles</span>
      </slot>
    </section>
    <section class="footer">
      <slot name="footer">
        <span>Sin acciones disponibles</span>
      </slot>
    </section>
  </article>
</template>

<style>
.tarjeta {
  width: 350px;
  height: auto;
  display: flex;
  flex-direction: column;
  gap: 10px;
  justify-content: space-between;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 10px;
  margin: 1rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;

  &.expandida {
    height: 350px;
  }

  .header {
    background-color: #f5c6c6;
    padding: 1rem;
    text-align: center;
  }
  .body {
    flex: 1;
    padding: 1rem;
    font-size: 16px;
  }
  .footer {
    background-color: #f5c6c6;
    padding: 1rem;
    text-align: center;
  }
}
</style>
