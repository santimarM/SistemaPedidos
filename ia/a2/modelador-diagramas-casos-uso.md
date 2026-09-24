# Documentación de uso de IA - Modelador de Diagramas de Casos de Uso

## Aclaración sobre este entregable
Este rol estaba asignado a Florencia Ivroud, quien se dio de baja de la materia. Para que el entregable no quede sin hacer, lo completó Santiago Medel (Documentador y Coordinador / Especialista en Escenarios), asumiendo un tercer rol por contingencia real, tal como permite la consigna de la Actividad N°2 ("si un integrante asume más de un rol por contingencias reales... y eso queda claramente documentado, podrá obtener un reconocimiento extra"). Se deja esta nota de forma transparente para no repetir el problema de atribución sin evidencia detectado y corregido en la Actividad N°1 (RC1/RC2).

## Herramienta utilizada
La consigna pide Copilot Agent Mode en VS Code. Se utilizó **Claude Code** (Anthropic) en su lugar, con la misma aclaración de transparencia ya documentada en `ia/a2/especialista-escenarios.md`.

## Archivos de contexto proporcionados al asistente
- `anexos/introduccion.md` (los 5 casos de uso completos: CU1-CU5, con actores, flujo, precondiciones y postcondiciones).

## Prompt utilizado (resumen)
"A partir de los 5 casos de uso documentados en introduccion.md, generá un diagrama PlantUML por cada uno, incluyendo el actor principal y al menos una relación de inclusión o extensión coherente con el flujo descripto."

## Ajustes realizados al output de la IA
- Se verificó que el actor de CU4 (Cancelar Pedido) fuera únicamente "Usuario de mostrador", sin incluir a "Encargado", ya que la corrección de RC43 en `anexos/introduccion.md` eliminó la transición Listo → Cancelado y con ella la necesidad de autorización del encargado.
- Se ajustaron las relaciones `<<include>>`/`<<extend>>` de cada diagrama para que reflejaran pasos reales del flujo principal de cada caso de uso (por ejemplo, "Registrar diferencia de pago" en CU2 se modeló como `<<extend>>` porque solo aplica condicionalmente, no siempre).
- Se renderizaron las imágenes `.png` localmente con PlantUML (plantuml.jar + Java) a partir de cada `.puml`, verificando visualmente que cada diagrama fuera legible antes de guardarlo.
