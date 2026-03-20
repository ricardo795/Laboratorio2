<script setup>
import { ref, computed } from 'vue';

// --- VARIABLES REACTIVAS (5) ---
const nombreCliente = ref('');            
const mensajeError = ref('');             
const pedidoConfirmado = ref(false);      
const inventario = ref([                  
  { id: 1, nombre: 'Café Rico (lb)', precio: 7.50, cantidad: 0 },
  { id: 2, nombre: 'Miel de Abeja (500ml)', precio: 5.25, cantidad: 0 },
  { id: 3, nombre: 'Queso Duro Blando (lb)', precio: 4.00, cantidad: 0 }
]);

// Variable reactiva computada para el total
const totalPedido = computed(() => {
  return inventario.value.reduce((acc, p) => acc + (p.precio * p.cantidad), 0);
});

// --- MÉTODO CON ALERTA DETALLADA ---
const validarYProcesar = () => {
  // 1. Validación de nombre vacío
  if (nombreCliente.value.trim() === "") {
    mensajeError.value = " El nombre del cliente es obligatorio.";
    pedidoConfirmado.value = false;
    return;
  }

  // 2. Validación de carrito vacío
  if (totalPedido.value <= 0) {
    mensajeError.value = "⚠️ Debes agregar al menos un producto al pedido.";
    pedidoConfirmado.value = false;
    return;
  }

  // 3. Si pasa las validaciones, generar resumen para la alerta
  mensajeError.value = "";
  pedidoConfirmado.value = true;

  // Filtrar solo productos con cantidad > 0
  let detalleProductos = "";
  inventario.value.forEach(p => {
    if (p.cantidad > 0) {
      detalleProductos += `- ${p.cantidad}x ${p.nombre} ($${(p.cantidad * p.precio).toFixed(2)})\n`;
    }
  });

  // Mostrar la alerta solicitada
  alert(`🛍️ ¡Pedido Confirmado!\n\nCliente: ${nombreCliente.value}\n\nProductos:\n${detalleProductos}\nTotal a pagar: $${totalPedido.value.toFixed(2)}`);
};
</script>

<template>
  <div class="container">
    <h1>🛒 La Tiendona 25/8</h1>

    <section class="cliente-info">
      <label>Nombre del Cliente:</label>
      <input 
        type="text" 
        v-model="nombreCliente" 
        placeholder="Escriba el nombre aquí..."
      >
    </section>

    <div class="productos">
      <div v-for="producto in inventario" :key="producto.id" class="card">
        <p><strong>{{ producto.nombre }}</strong></p>
        <p>Precio: ${{ producto.precio.toFixed(2) }}</p>
        <input 
          type="number" 
          v-model.number="producto.cantidad" 
          min="0"
        >
      </div>
    </div>

    <p v-if="mensajeError" class="error">{{ mensajeError }}</p>

    <div class="total-section">
      <h3>Total Estimado: ${{ totalPedido.toFixed(2) }}</h3>
      <button @click="validarYProcesar">Confirmar Pedido</button>
    </div>

    <article v-if="pedidoConfirmado" class="resumen">
      <h2>✅ Registro Exitoso</h2>
      <p>El pedido de <strong>{{ nombreCliente }}</strong> ha sido enviado.</p>
    </article>
  </div>
</template>

<style scoped>
.container {
     font-family: sans-serif;
     max-width: 500px;
     margin: auto;
     padding: 20px;
     background-color: #f9f9f9;
     border-radius: 15px; }
.card {
     border: 1px solid #ddd; 
     padding: 15px; 
     margin-bottom: 10px; 
     border-radius: 10px; 
     background: white; }
.error { 
    color: #d9534f; 
    font-weight: bold; 
    background: #f2dede; 
    padding: 10px; 
    border-radius: 5px; }
.resumen { 
    margin-top: 20px; 
    padding: 15px; 
    background-color: #dff0d8; 
    border: 1px solid #d6e9c6; 
    border-radius: 10px; }
input[type="text"], input[type="number"] { width: 100%; padding: 10px; margin-top: 5px; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; }
button { width: 100%; background-color: #007bff; color: white; border: none; padding: 12px; cursor: pointer; border-radius: 5px; font-weight: bold; font-size: 16px; }
button:hover { background-color: #0056b3; }
</style>