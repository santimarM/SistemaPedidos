# Escenario de Caso de Uso: Cocina avanza el pedido de Recibido a Listo

- **Nombre del caso de uso:** CU3 - Cambiar Estado del Pedido
- **ID única:** EC-03
- **Área:** Cocina
- **Actor(es):** Cocina
- **Descripción:** Cocina informa el avance de preparación de un pedido y el sistema actualiza su estado respetando las transiciones válidas del ciclo de vida (Recibido → En preparación → Listo).
- **Evento activador:** Cocina comienza físicamente a preparar un pedido de la lista de pendientes.
- **Tipo de señal:** Externa (acción manual del personal de cocina sobre el sistema).
- **Pasos desempeñados (ruta principal):**
  1. Cocina consulta los pedidos pendientes según su estado actual.
  2. Cocina indica que comienza a preparar un pedido.
  3. El sistema valida que la transición sea válida (Recibido → En preparación) y actualiza el estado.
  4. Cocina indica que el pedido está terminado.
  5. El sistema valida la transición (En preparación → Listo) y actualiza el estado.
  6. El sistema bloquea cualquier modificación del pedido a partir de este punto.
- **Precondiciones:**
  - El pedido existe y tiene un estado que admite la transición solicitada.
- **Postcondiciones:**
  - El pedido queda en un único estado actual, consistente y visible tanto para mostrador como para cocina.
- **Suposiciones:**
  - Cocina y mostrador consultan el mismo sistema, sin pizarras físicas paralelas que puedan desincronizarse.
- **Reunir requerimientos:** Cubre RF3 (seguimiento y visualización del estado del pedido).
- **Aspectos sobresalientes:** ¿Qué pasa si cocina intenta marcar "Listo" un pedido que nunca pasó por "En preparación"? El sistema debe rechazar transiciones que salten pasos.
- **Prioridad:** Alta
- **Riesgo:** Alto (este caso de uso ataca directamente el problema real detectado: un mismo pedido apareciendo en dos columnas distintas de la pizarra).
