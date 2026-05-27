<script setup>
import { computed, ref } from "vue";
import TabElectronica from "./components/tabs/TabElectronica.vue";
import TabPerifericos from "./components/tabs/TabPerifericos.vue";
import TabTodos from "./components/tabs/TabTodos.vue";

const tabs = {
  todos: TabTodos,
  electronica: TabElectronica,
  perifericos: TabPerifericos,
};

const tabSinKeepAlive = ref("todos");
const tabConKeepAlive = ref("todos");

const componenteSinKeepAlive = computed(() => tabs[tabSinKeepAlive.value]);
const componenteConKeepAlive = computed(() => tabs[tabConKeepAlive.value]);
</script>

<template>
  <section class="panel-pestanas">
    <h2>Panel de pestanas</h2>

    <div class="comparador">
      <article class="bloque">
        <h3>Sin KeepAlive</h3>
        <div class="controles">
          <button @click="tabSinKeepAlive = 'todos'">Todos</button>
          <button @click="tabSinKeepAlive = 'electronica'">Electronica</button>
          <button @click="tabSinKeepAlive = 'perifericos'">Perifericos</button>
        </div>
        <component :is="componenteSinKeepAlive" />
      </article>

      <article class="bloque">
        <h3>Con KeepAlive</h3>
        <div class="controles">
          <button @click="tabConKeepAlive = 'todos'">Todos</button>
          <button @click="tabConKeepAlive = 'electronica'">Electronica</button>
          <button @click="tabConKeepAlive = 'perifericos'">Perifericos</button>
        </div>
        <KeepAlive>
          <component :is="componenteConKeepAlive" />
        </KeepAlive>
      </article>
    </div>
  </section>
</template>

<style scoped>
.panel-pestanas {
  padding: 1rem;
}

.comparador {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 1rem;
}

.bloque {
  border: 1px solid #d8d8d8;
  border-radius: 8px;
  padding: 1rem;
  background: #f9f9f9;
}

.controles {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
</style>
