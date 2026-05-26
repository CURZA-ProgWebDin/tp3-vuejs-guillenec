<script setup>
import { productos } from "./data/productos.js";
import TarjetaProducto from "./components/TarjetaProducto.vue";

const p1 = productos[0];
const p2 = productos[1];
const p3 = productos[2];
</script>

<template>
  <div class="base-layout">
    <section class="contain-cards">
      <TarjetaProducto>
        <template #header>
          <h2 class="title">{{ p1.nombre }}</h2>
          <h3 class="category">{{ p1.categoria }}</h3>
        </template>
        <template #body="{ expandida, toggleExpandir }">
          <button @click="toggleExpandir">
            {{ expandida ? "Ver menos" : "Ver más" }}
          </button>
          <div class="info-producto" v-if="expandida">
            <p class="price">Precio: {{ p1.precio }}</p>
            <p class="stock">Stock: {{ p1.stock }}</p>
          </div>
        </template>
        <template #footer>
          <button>Comprar Ahora</button>
        </template>
      </TarjetaProducto>
      <!-- tarjeta sin footer -->
      <TarjetaProducto>
        <template #header>
          <h2 class="title">{{ p2.nombre }}</h2>
          <h3 class="category">{{ p2.categoria }}</h3>
        </template>
        <template #body="{ expandida, toggleExpandir }">
          <button @click="toggleExpandir">
            {{ expandida ? "Ver menos" : "Ver más" }}
          </button>
          <div class="info-producto" v-if="expandida">
            <p class="price">Precio: {{ p2.precio }}</p>
            <p class="stock">Stock: {{ p2.stock }}</p>
          </div>
        </template>
      </TarjetaProducto>
      <TarjetaProducto>
        <template #header>
          <h2 class="title">{{ p3.nombre }}</h2>
          <h3 class="category">{{ p3.categoria }}</h3>
        </template>
        <template #body="{ expandida, toggleExpandir }">
          <button @click="toggleExpandir">
            {{ expandida ? "Ver menos" : "Ver más" }}
          </button>
          <div class="info-producto" v-if="expandida">
            <p class="price">Precio: {{ p3.precio }}</p>
            <p class="stock">Stock: {{ p3.stock }}</p>
          </div>
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
    align-items: flex-start;
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
.info-producto {
  margin-top: 1rem;
  height: 100px;
}
</style>
