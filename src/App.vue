<script setup>
import { productos } from "./data/productos.js";
import TarjetaProducto from "./components/TarjetaProducto.vue";

const itemProducto = {
  nombre: "Producto Destacado",
  categoria: "Electrónica",
  precio: "$99.99",
  stock: 20,
};
</script>

<template>
  <div class="base-layout">
    <section class="contain-cards">
      <TarjetaProducto v-for="producto in productos" :key="producto.id">
        <template #header>
          <h2 class="title">{{ producto.nombre }}</h2>
          <h3 class="category">{{ producto.categoria }}</h3>
        </template>
        <template #body>
          <p class="price">Precio: {{ producto.precio }}</p>
          <p class="stock">Stock: {{ producto.stock }}</p>
        </template>
        <template #footer>
          <button>Comprar Ahora</button>
        </template>
      </TarjetaProducto>
    </section>
  </div>
</template>

<style>
.base-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-color: azure;

  .contain-cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    padding: 2rem;
  }
}

.title {
  color: #441c1c;
  margin-bottom: 0.5rem;
}
.category {
  color: #8b0000;
  margin-bottom: 1rem;
}
.price {
  color: #2e7d32;
  font-weight: bold;
  margin-bottom: 0.5rem;
}
.stock {
  color: #1565c0;
}
button {
  background-color: #8b0000;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #5a0000;
}
</style>
