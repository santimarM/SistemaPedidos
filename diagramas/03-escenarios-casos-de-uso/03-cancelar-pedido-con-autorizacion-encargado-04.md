# Escenario de Caso de Uso: Cancelación de un pedido en estado Listo con autorización del encargado

- **Nombre del caso de uso:** CU4 - Cancelar Pedido
- **ID única:** EC-04
- **Área:** Mostrador / Excepciones de negocio
- **Actor(es):** Usuario de mostrador, Encargado
- **Descripción:** El usuario de mostrador cancela un pedido que ya está en estado "Listo", lo que requiere la autorización del encargado antes de aplicar el cambio, conservando el registro histórico.
- **Evento activador:** El cliente no retira el pedido o se arrepiente luego de que cocina ya lo terminó.
- **Tipo de señal:** Externa (decisión del cliente comunicada al usuario de mostrador).
- **Pasos desempeñados (ruta principal):**
  1. El usuario de mostrador selecciona el pedido a cancelar.
  2. El sistema verifica el estado actual del pedido.
  3. Como el pedido está en "Listo", el sistema requiere la autorización del encargado antes de cancelar.
  4. El encargado autoriza la cancelación.
  5. El sistema cambia el estado del pedido a "Cancelado".
  6. El sistema conserva el pedido y su historial (no lo elimina).
- **Precondiciones:**
  - El pedido no se encuentra en estado "Entregado".
  - El pedido está en estado "Listo" (condición que dispara el requisito de autorización).
- **Postcondiciones:**
  - El pedido queda en estado "Cancelado", visible en el historial, sin volver nunca a un estado de preparación.
- **Suposiciones:**
  - Hay un encargado disponible en el turno para autorizar la excepción.
- **Reunir requerimientos:** Cubre RF5 (cancelación completa del pedido).
- **Aspectos sobresalientes:** ¿Cómo queda registrada la identidad del encargado que autorizó, a fines de trazabilidad? ¿Debe pedirse un motivo de cancelación?
- **Prioridad:** Media
- **Riesgo:** Medio (si no se aplica bien la regla de autorización, se podría cancelar sin control un pedido que la cocina ya completó, generando pérdida de insumos).
