# Documentación de uso de IA - Especialista en Escenarios de Casos de Uso

## Herramienta utilizada
La consigna pide usar Copilot Agent Mode en VS Code. Para esta tarea se utilizó en su lugar **Claude Code** (Anthropic), operando como agente dentro de VS Code sobre este mismo repositorio. Se deja esta aclaración de forma transparente porque el asistente de IA efectivamente usado no fue GitHub Copilot.

## Archivos de contexto proporcionados al asistente
- `anexos/introduccion.md` (requisitos funcionales y no funcionales, y resumen de los 5 casos de uso).
- `modelador de caso de uso/casos_de_uso.md` (detalle completo de actores, flujo principal, precondiciones y postcondiciones de CU1-CU5).
- Los campos exigidos por la plantilla de Escenarios de Caso de Uso descriptos en la consigna de la Actividad Obligatoria N°2 (ID única, área, actores, descripción, evento activador, tipo de señal, pasos, precondiciones, postcondiciones, suposiciones, requerimientos, aspectos sobresalientes, prioridad y riesgo).

## Prompt utilizado (resumen)
"A partir de los 5 casos de uso documentados en introduccion.md y casos_de_uso.md, generá un escenario de caso de uso por cada uno (EC-01 a EC-05), completando todos los campos de la plantilla de la Actividad N°2: ID única, área, actores, descripción, evento activador, tipo de señal, pasos de la ruta principal, precondiciones, postcondiciones, suposiciones, requerimientos que cubre, aspectos sobresalientes, prioridad y riesgo."

## Ajustes realizados al output de la IA
- Se revisó que cada escenario reflejara el flujo "feliz" (ruta principal) del caso de uso correspondiente, sin mezclar flujos alternativos que no estaban documentados en la Actividad N°1.
- Se ajustó el campo "Riesgo" de cada escenario para que estuviera justificado con un motivo concreto (por ejemplo, condición de carrera en CU2, o el problema real de la pizarra de cocina en CU3), en vez de dejar una etiqueta sin fundamento.
- Se revisaron las "Aspectos sobresalientes" para que fueran preguntas abiertas genuinamente no resueltas en la documentación existente, y no afirmaciones ya cubiertas por las precondiciones.
- Se verificó que el campo "Reunir requerimientos" de cada escenario apuntara a un RF concreto de `anexos/introduccion.md`, en vez de una referencia genérica.
