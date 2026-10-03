# Diseñador de Tarjetas CRC

## Prompt utilizado

Se utilizó Copilot Agent Mode en VS Code con el siguiente prompt:

> Leé como contexto los siguientes archivos del proyecto:
>
> - anexos/introduccion.md
> - diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw
>
> A partir de estos archivos, identificá todas las clases presentes en el boceto de clases y proponé una tarjeta CRC para cada una.
>
> Para cada tarjeta indicá:
> - Nombre de la clase
> - Superclase/subclase, si corresponde
> - Pensamiento del objeto
> - Responsabilidades principales
> - Colaboraciones
> - Propiedades
>
> No agregues clases, responsabilidades, relaciones ni reglas de negocio que no estén justificadas por los archivos de contexto.
>
> No modifiques ningún archivo del repositorio todavía. Mostrame únicamente la propuesta para que pueda revisarla críticamente antes de implementarla.

## Archivos de contexto

Para generar la propuesta inicial con Copilot se utilizaron los siguientes archivos:

- `anexos/introduccion.md`, incluyendo los casos de uso documentados en el archivo.
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`

Durante la revisión crítica, los casos de uso de `anexos/introduccion.md` se utilizaron para validar las responsabilidades y colaboraciones propuestas para las clases.

## Revisión crítica y ajustes realizados

La propuesta generada por Copilot fue revisada antes de crear las tarjetas CRC definitivas.

Se realizaron los siguientes ajustes:

- Se verificaron las clases propuestas contra el boceto de clases y los casos de uso documentados.
- Se descartaron como tarjetas CRC `EstadoPedido`, `EstadoComanda` y `MetodoPago`, ya que aparecen como tipos utilizados por atributos y no como clases del boceto.
- No se asignaron superclases ni subclases, porque el boceto actual no presenta relaciones de herencia.
- Se revisaron las colaboraciones propuestas para evitar considerar automáticamente cada asociación del diagrama como una colaboración CRC. Se conservaron únicamente aquellas necesarias para cumplir una responsabilidad.
- Se ajustaron responsabilidades para representar comportamientos o propósitos de las clases y evitar agregar operaciones que no aparecen justificadas por el modelo o los casos de uso.
- En `ItemPedido` se definió la responsabilidad de determinar su subtotal a partir de su cantidad y precio unitario, considerando el costo adicional de las personalizaciones. Se mantuvo `Personalizacion` como colaborador para esta responsabilidad.
- Se evitó agregar propiedades a `Usuario` que no existen en el boceto. Por este motivo, las responsabilidades de `Usuario` que requieren interactuar con otros objetos no poseen una propiedad propia asociada cuando el modelo no la define.
- Se revisó la dirección de las colaboraciones. Por ejemplo, `ItemPedido` necesita información de `Personalizacion` para considerar su costo adicional, pero `Personalizacion` no necesita colaborar con `ItemPedido` para conocer su propio costo.
- Se descartaron responsabilidades, propiedades y colaboraciones que no pudieron justificarse mediante los archivos utilizados como contexto.
## Corrección posterior por contingencia (PR de corrección de tarjetas CRC)

La code review del Documentador y Coordinador sobre la PR #53 detectó tres problemas: `03-tarjeta-crc-item-pedido.md` quedó vacío, la columna Propiedad de `01-tarjeta-crc-usuario.md` estaba sin completar y el índice `herramientas_agile.md` enlazaba a la carpeta en lugar de a cada tarjeta. Ante la falta de respuesta de la Diseñadora de Tarjetas CRC antes del cierre de la entrega, las correcciones las aplicó Santiago Medel (Documentador y Coordinador), asistido por **Claude Code** (Anthropic) en VS Code.

**Prompt utilizado (resumen):** "Completá la tarjeta CRC de `ItemPedido` respetando la plantilla y el diseño ya documentado en `ia/a2/disenador-tarjetas-crc.md`; completá la columna Propiedad de `Usuario` sin agregarle atributos que no existan en el boceto; y armá el índice de `herramientas_agile.md` con un enlace por tarjeta. Usá solo atributos y relaciones de `01-boceto-inicial.excalidraw` y de `anexos/introduccion.md`."

**Archivos de contexto:** `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`, `anexos/introduccion.md`, las tarjetas 02 y 04-09 como referencia de formato, y este mismo archivo.

**Ajustes y criterios aplicados:**
- La tarjeta de `ItemPedido` se armó siguiendo el diseño ya definido por la Diseñadora en la revisión crítica anterior: una única responsabilidad (determinar el subtotal a partir de `cantidad` y `precioUnitario`, considerando el costo adicional de las personalizaciones) con `Personalizacion` como colaborador. No se agregaron colaboraciones con `Producto` o `Combo` porque `ItemPedido` ya conoce su propio `precioUnitario` y no necesita consultarlos para esa responsabilidad.
- En `Usuario` se mantuvo el criterio de no agregar atributos inexistentes en el boceto. La columna Propiedad se completó con la propiedad del colaborador que cada responsabilidad utiliza (`Pedido.referenciaRetiro`, `Pedido.estado`, `Pedido.prioridad`, `Pago.monto`), según los casos de uso CU1-CU5.
- El índice se reescribió con un enlace por tarjeta, siguiendo el ejemplo de la consigna.
