<script setup></script>

<template>
  <div class="base-layout">
    <header class="header">
      <slot name="header"></slot>
    </header>
    <main class="main">
      <slot name="main"></slot>
    </main>
    <footer class="footer">
      <slot name="footer"></slot>
      <p>&copy; 2024 Mi Aplicación Vue. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>

<style>
.base-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;

  .header {
    background-color: #d24040;
    padding: 1rem;
  }

  .main {
    background-color: #f5c6c6;
    flex: 1;
    padding: 1rem;
    color: #333;

    h2 {
      color: #441c1c;
      margin-top: 1rem;
    }
  }

  .footer {
    background-color: #441c1c;
    padding: 1rem;
    text-align: center;
  }
}
</style>
