<script setup></script>

<template>
  <article class="tarjeta">
    <h2 class="header">
      <slot name="header">
        <span>Sin acciones disponibles</span>
      </slot>
    </h2>
    <section class="body">
      <slot name="body">
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
  height: 400px;
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

  .header {
    background-color: #f5c6c6;
    padding: 1rem;
    text-align: center;
    color: #333;
    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    font-size: 20px;
  }
  .body {
    flex: 1;
    padding: 1rem;
    color: #333;
    font-family: "Arial", sans-serif;
    font-size: 16px;
  }
  .footer {
    background-color: #f5c6c6;
    padding: 1rem;
    text-align: center;
    color: #333;
    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    font-size: 18px;
  }
}
</style>
