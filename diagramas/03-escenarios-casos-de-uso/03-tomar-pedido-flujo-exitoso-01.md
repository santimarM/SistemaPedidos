# Escenario de Caso de Uso: Toma de pedido con confirmación exitosa

- **Nombre del caso de uso:** CU1 - Tomar Pedido
- **ID única:** EC-01
- **Área:** Mostrador / Toma de pedidos
- **Actor(es):** Usuario de mostrador
- **Descripción:** El usuario de mostrador registra un pedido nuevo con productos, cantidades y personalizaciones; el sistema calcula el total y lo envía automáticamente a cocina en estado "Recibido".
- **Evento activador:** El cliente se acerca al mostrador y solicita realizar un pedido.
- **Tipo de señal:** Externa (iniciada por la interacción del usuario de mostrador con el sistema).
- **Pasos desempeñados (ruta principal):**
  1. El usuario de mostrador inicia un nuevo pedido en el sistema.
  2. El sistema genera un número de pedido y solicita una referencia de retiro.
  3. El usuario agrega productos o combos con sus cantidades y personalizaciones.
  4. El sistema calcula el precio de cada ítem y el total del pedido.
  5. El usuario confirma el pedido.
  6. El sistema fija el estado como "Recibido" y envía la comanda a cocina.
- **Precondiciones:**
  - El local está operativo.
  - El usuario está autenticado en el sistema.
- **Postcondiciones:**
  - El pedido queda registrado con número único, ítems, total y estado "Recibido".
  - Cocina recibe la comanda sin intervención manual adicional.
- **Suposiciones:**
  - El catálogo de productos y combos está actualizado al momento de tomar el pedido.
  - La conexión entre mostrador y cocina está disponible.
- **Reunir requerimientos:** Cubre RF1 (toma de pedidos con personalizaciones y combos) y RF2 (envío automático de comandas a cocina).
- **Aspectos sobresalientes:** ¿Qué ocurre si se agrega una personalización no contemplada en el catálogo? ¿El sistema debe permitir pedidos sin referencia de retiro?
- **Prioridad:** Alta
- **Riesgo:** Medio (es el punto de entrada de todo el flujo; un error aquí afecta a todo el ciclo de vida del pedido).
