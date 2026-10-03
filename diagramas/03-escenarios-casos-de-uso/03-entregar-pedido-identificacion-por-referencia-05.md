# Escenario de Caso de Uso: Entrega de un pedido identificado por nombre de retiro

- **Nombre del caso de uso:** CU5 - Entregar Pedido
- **ID única:** EC-05
- **Área:** Mostrador / Entrega
- **Actor(es):** Usuario de mostrador
- **Descripción:** El usuario de mostrador identifica el pedido por su número o nombre de retiro y lo entrega al cliente, quedando registrado como finalizado.
- **Evento activador:** El cliente se presenta en el mostrador para retirar su pedido.
- **Tipo de señal:** Externa (llegada física del cliente al mostrador).
- **Pasos desempeñados (ruta principal):**
  1. El cliente se presenta en el mostrador y menciona su nombre de retiro o número de pedido.
  2. El usuario de mostrador busca el pedido en el sistema por número o referencia.
  3. El sistema muestra el pedido y confirma que su estado es "Listo".
  4. El usuario de mostrador entrega el pedido físicamente al cliente.
  5. El usuario confirma la entrega en el sistema.
  6. El sistema cambia el estado del pedido a "Entregado".
- **Precondiciones:**
  - El pedido existe y su estado actual es "Listo".
- **Postcondiciones:**
  - El pedido queda en estado "Entregado" de forma definitiva (ya no admite cancelación ni modificación).
- **Suposiciones:**
  - El nombre o número de retiro que da el cliente es suficiente para ubicar el pedido sin ambigüedad.
- **Reunir requerimientos:** Cubre RF6 (identificación del pedido para el retiro).
- **Aspectos sobresalientes:** ¿Qué pasa si dos clientes coinciden en el mismo nombre de retiro? ¿Debe exigirse el número de pedido como respaldo?
- **Prioridad:** Alta
- **Riesgo:** Bajo (es el último paso del flujo feliz y depende de datos ya validados en pasos anteriores).
