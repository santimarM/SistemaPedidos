# Escenario de Caso de Uso: Cancelación de un pedido

- **Nombre del caso de uso:** CU4 - Cancelar Pedido
- **ID única:** EC-04
- **Área:** Mostrador / Excepciones de negocio
- **Actor(es):** Usuario de mostrador, Encargado
- **Descripción:** El usuario de mostrador cancela un pedido que aún no fue entregado. Solo se permite cancelar si el pedido está en estado "Recibido" o "En preparación". Si el pedido ya está "Listo", la cancelación no está permitida y el pedido debe entregarse o registrarse como no retirado.
- **Evento activador:** El cliente se arrepiente antes de que el pedido esté listo o solicita cancelarlo antes de que cocina lo termine.
- **Tipo de señal:** Externa (decisión del cliente comunicada al usuario de mostrador).
- **Pasos desempeñados (ruta principal):**
  1. El usuario de mostrador selecciona el pedido a cancelar.
  2. El sistema verifica el estado actual del pedido.
  3. Si el pedido está en "Recibido" o "En preparación", el sistema permite continuar.
  4. Si el pedido está en "Listo", el sistema rechaza la cancelación e informa que debe entregarse.
  5. El sistema cambia el estado del pedido a "Cancelado".
  6. El sistema registra la cancelación en la auditoría (usuario, fecha, hora).
  7. El sistema conserva el pedido y su historial (no lo elimina).
- **Precondiciones:**
  - El pedido existe.
  - El pedido está en estado "Recibido" o "En preparación".
- **Postcondiciones:**
  - El pedido queda en estado "Cancelado", visible en el historial.
  - Se liberan los recursos asociados a la preparación.
  - Queda registro en auditoría.
- **Suposiciones:**
  - No se requiere autorización del encargado porque la cancelación solo aplica antes de que el pedido esté listo.
- **Reunir requerimientos:** Cubre RF5 (cancelación completa del pedido).
- **Aspectos sobresalientes:** ¿Cómo queda registrada la identidad del usuario que canceló, a fines de trazabilidad? ¿Debe pedirse un motivo de cancelación?
- **Prioridad:** Media
- **Riesgo:** Bajo (la regla impide cancelar pedidos ya listos, evitando pérdida de insumos).
