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