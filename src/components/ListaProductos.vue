<script setup>
import {
  ref,
  useTemplateRef,
  onMounted,
  onUpdated,
  onBeforeUnmount,
} from "vue";
import TarjetaProducto from "./TarjetaProducto.vue";

const props = defineProps({
  productos: {
    type: Array,
    required: true,
  },
});
const cargando = ref(false);
const productosRender = ref([]);
const box = useTemplateRef("box");

let timer = null;

function esperar(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function cargarProductos() {
  cargando.value = true;
  await esperar(800);
  productosRender.value = props.productos;
  cargando.value = false;
}

onMounted(() => {
  cargarProductos();
  timer = setInterval(cargarProductos, 30000);
});

onUpdated(() => {
  if (box.value) {
    box.value.scrollTop = box.value.scrollHeight;
  }
});

onBeforeUnmount(() => {
  clearInterval(timer);
  console.log("ListaProductos desmontado - polling detenido");
});
</script>

<template>
  <section class="contenedor-lista">
    <p v-if="cargando" class="estado">Cargando...</p>
    <div v-else ref="box" class="lista">
      <TarjetaProducto v-for="producto in productosRender" :key="producto.id">
        <template #header>
          <h3>{{ producto.nombre }}</h3>
          <p>{{ producto.categoria }}</p>
        </template>
        <template #body="{ expandida, toggleExpandir }">
          <button @click="toggleExpandir">
            {{ expandida ? "Ver menos" : "Ver mas" }}
          </button>
          <div v-if="expandida" class="detalle">
            <p>Precio: {{ producto.precio }}</p>
            <p>Stock: {{ producto.stock }}</p>
          </div>
        </template>
        <template #footer>
          <button>Comprar</button>
        </template>
      </TarjetaProducto>
    </div>
  </section>
</template>
<style scoped>
.contenedor-lista {
  width: 100%;
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;

  .estado {
    font-weight: 600;
    height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .lista {
    max-height: 520px;
    overflow-y: auto;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 0.75rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    align-items: flex-start;
  }
}

.detalle {
  margin-top: 0.75rem;
}
</style>
