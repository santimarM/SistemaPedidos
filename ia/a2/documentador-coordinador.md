# Documentación de uso de IA - Documentador y Coordinador de Repositorio

## Herramienta utilizada
La consigna pide usar Copilot Agent Mode en VS Code. Para las tareas de coordinación se utilizó **Claude Code** (Anthropic), operando como agente dentro de VS Code sobre este mismo repositorio. Se deja esta aclaración de forma transparente, igual que en `ia/a2/especialista-escenarios.md`.

## Archivos de contexto proporcionados al asistente
- `anexos/introduccion.md`: requisitos funcionales y no funcionales, casos de uso CU1-CU5 y modelo de dominio de la Actividad N°1.
- `changelog.md` y `.github/PULL_REQUEST_TEMPLATE/`: formato de registro y templates de PR exigidos.
- Los comentarios de review del docente en la PR #20 (RC1-RC72) y la consigna de la Actividad Obligatoria N°2.

## Tareas de coordinación asistidas con IA

### Resolución de correcciones de la Actividad N°1
- **Prompt (resumen):** "Leé los Request Changes del docente en la PR #20 y en las PRs de fix, aplicá cada corrección en una rama `fix/` creada desde `release/actividad-obligatoria-1`, registrá la PR en `changelog.md` bajo `[Fixed]` reproduciendo literalmente su título y enlazando el número real de PR."
- **Ajustes realizados al output:**
  - Cuando la PR revisada ya estaba mergeada (PR #46), se abrió una PR nueva (#47) en lugar de sumar commits a una rama ya integrada.
  - Se verificó por API el título literal de cada PR contra su entrada del changelog; se corrigieron las entradas de las PRs #42 y #46 que no coincidían.
  - Las descripciones históricas de las PRs (RC13) se reescribieron con los templates dejando sin tildar los ítems del checklist que no se cumplieron, en lugar de marcarlos todos como cumplidos.

### Backport de la release hacia `develop`
- **Prompt (resumen):** "Realizá el backport de la release aprobada hacia `develop` según la consigna."
- **Ajustes realizados al output:** el primer intento (PR #49) creó la rama de backport desde `develop` antes de mergear la release, lo que no respeta el paso 7 de la consigna. Se cerró, se mergeó primero la PR #20 a `master` y se recreó `backport/release-actividad-obligatoria-1` desde `master` actualizado (PR #50). El conflicto en `changelog.md` se resolvió conservando el changelog de la release y moviendo la entrada de la PR #30 a `[Unreleased]` con sus enlaces reales.

### Integración de features en `develop`
- La PR #44 se actualizó sobre el nuevo `develop` y se reorganizó en un único commit para permitir el *rebase and merge* que pide la consigna.

## Code reviews asistidas con IA

**Prompt base utilizado en cada review:**

> "Leé `anexos/introduccion.md` como contexto (requisitos funcionales y no funcionales, casos de uso CU1-CU5 y modelo de dominio de la Actividad N°1). Revisá el diff de la PR #N y verificá: (1) que el entregable sea coherente con los requisitos y casos de uso definidos; (2) que respete la estructura de carpetas y el naming de la consigna; (3) que incluya el archivo `ia/a2/[rol].md` completo, con prompt, archivos de contexto y ajustes; (4) que la PR esté registrada en `changelog.md` con rama, autor y rol. Señalá cada problema indicando archivo y línea del diff."

| PR | Autor | Prompt / foco de la review | Hallazgos cargados en el diff | Resultado |
|---|---|---|---|---|
| | | | | |

## Contingencias
El grupo quedó con dos integrantes activos (ver `changelog.md`). Por eso las code reviews del Documentador y Coordinador solo pueden realizarse sobre las PRs de la otra integrante activa, y las PRs propias del Documentador son aprobadas por ella.
