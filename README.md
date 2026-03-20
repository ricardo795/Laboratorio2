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
