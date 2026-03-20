# Sistema de Gestión de Pedidos: "La Tiendona 25/8"

 Situación Problemática
En el municipio de San Miguel, muchos pequeños emprendedores de productos orgánicos y artesanales gestionan sus pedidos a través de mensajes de texto dispersos. Esto genera pérdida de información, errores en las entregas y falta de control sobre el inventario disponible en tiempo real. Los clientes no tienen una forma clara de ver qué hay disponible y los vendedores se saturan respondiendo las mismas dudas sobre precios.

 Sector Enfocado
- Comercio Minorista (Retail):** Pequeñas empresas y emprendedores locales.
-  **Logística de Distribución:** Optimización de la toma de pedidos.

Solución Propuesta
Se desarrolla una aplicación web reactiva utilizando **Vue.js** que permite:
1.  Visualizar un catálogo dinámico de productos.
2.  Calcular en tiempo real el costo total de un pedido según la cantidad ingresada.
3.  Validar que los datos del cliente y las cantidades sean correctos antes de procesar.
4.  Gestionar estados de visibilidad mediante directivas para mejorar la experiencia de usuario.


Respuesta de preguntas:

1 - ¿Qué es Vue.js y cuál es su función en esta página?
Vue.js es un framework de JavaScript diseñado para crear interfaces de usuario de forma sencilla y eficiente. En esta aplicación, su función es actuar como el "motor" que conecta los datos con lo que el usuario ve. Gracias a Vue, la página no necesita recargarse cada vez que el usuario escribe un nombre o cambia una cantidad; la interfaz reacciona al instante, permitiendo una experiencia fluida y profesional.

2 - Variables reactivas utilizadas y su función
En el sistema implementamos las siguientes 5 variables para controlar el flujo de información:

nombreCliente: Captura el texto del input para identificar a quién pertenece el pedido.

inventario: Es un arreglo de objetos que contiene la "fuente de verdad" del catálogo (nombres, precios y cantidades seleccionadas).

mensajeError: Almacena las alertas de validación que se muestran si el usuario intenta enviar el formulario incompleto.

pedidoConfirmado: Funciona como un interruptor (booleano) que decide cuándo mostrar el resumen final de la compra.

totalPedido: Es una variable computada que se encarga de hacer la matemática pesada (multiplicar precios por cantidades) cada vez que el inventario cambia.

3 - Diferencia entre v-bind y v-model
Aunque ambas sirven para conectar datos, funcionan de manera distinta:

v-bind (Enlace unidireccional): Se usa para enviar información desde el código hacia un atributo de HTML (como un id, una class o una key). La información viaja en un solo sentido: del script a la vista.

v-model (Enlace bidireccional): Se usa específicamente en elementos de formulario (inputs, selects). Crea un canal de doble vía: si el usuario escribe en el input, la variable en el código se actualiza automáticamente; y si el código cambia la variable, el texto en el input también cambia.
