# Escenario de Caso de Uso: Corrección de un pedido antes de iniciar preparación

- **Nombre del caso de uso:** CU2 - Modificar Pedido
- **ID única:** EC-02
- **Área:** Mostrador / Gestión de pedidos activos
- **Actor(es):** Usuario de mostrador
- **Descripción:** El usuario de mostrador corrige un pedido ya tomado (agrega, quita o cambia ítems/personalizaciones) mientras cocina todavía no comenzó a prepararlo.
- **Evento activador:** El cliente solicita un cambio sobre un pedido que ya fue confirmado.
- **Tipo de señal:** Externa (solicitud del cliente transmitida por el usuario de mostrador).
- **Pasos desempeñados (ruta principal):**
  1. El usuario de mostrador selecciona el pedido existente a modificar.
  2. El sistema valida que el pedido esté en estado "Recibido".
  3. El usuario modifica ítems y/o personalizaciones.
  4. El sistema recalcula el total del pedido.
  5. Si el pedido ya tenía un pago registrado, el sistema deja constancia de la diferencia a cobrar.
  6. El sistema conserva el mismo número de pedido (no se crea uno nuevo).
- **Precondiciones:**
  - El pedido existe y su estado actual es "Recibido".
- **Postcondiciones:**
  - El pedido queda actualizado con los nuevos ítems/personalizaciones y el total recalculado.
  - Si corresponde, queda registrada una diferencia pendiente de cobro.
- **Suposiciones:**
  - Cocina consulta el estado antes de comenzar a preparar, por lo que la ventana de modificación es real y no meramente teórica.
- **Reunir requerimientos:** Cubre RF4 (modificación de pedidos activos antes de la preparación).
- **Aspectos sobresalientes:** ¿Cómo se notifica al cliente la diferencia a cobrar si ya había pagado? ¿Debe bloquearse la modificación apenas cocina "toma" visualmente el pedido, aunque el estado formal siga en "Recibido"?
- **Prioridad:** Alta
- **Riesgo:** Alto (una condición de carrera entre "cocina empieza a preparar" y "mostrador modifica" puede generar inconsistencias si no se sincroniza bien el cambio de estado).
