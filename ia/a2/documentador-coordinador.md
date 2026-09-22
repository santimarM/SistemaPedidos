# Documentación de uso de IA - Documentador y Coordinador de Repositorio

## Herramienta utilizada
La consigna pide usar Copilot Agent Mode en VS Code para las code reviews. En su lugar se utilizó **Claude Code** (Anthropic) dentro de VS Code, con acceso de lectura al repositorio completo y a las páginas de las Pull Requests en GitHub. Se deja esta aclaración de forma transparente, en la misma línea que lo documentado en `ia/a2/especialista-escenarios.md`.

## Metodología de las code reviews
Para cada PR revisada se pidió al asistente que:
1. Leyera `anexos/introduccion.md` (requisitos, casos de uso y modelo de dominio) como referencia de coherencia.
2. Obtuviera el diff real de la PR (no solo el resumen de GitHub) comparando los commits del merge, para verificar el contenido efectivamente cambiado.
3. Verificara, para fixes sobre el diagrama de clases, el contenido textual del archivo `.excalidraw` (extrayendo las etiquetas de texto de cada clase) en vez de confiar únicamente en la descripción de la PR.
4. Señalara cualquier incoherencia entre el diagrama, `introduccion.md` y los casos de uso.

## Code Review 1 — PR #22 "fix: corregir boceto inicial de clases (RC7-RC10)" (autora: @neith18)
**Revisión:** Se comparó el commit de merge (4bbbb04) contra su base. Cambios verificados:
- Se eliminaron `01-boceto-inicial-clases.puml` (154 líneas) y `01-boceto-inicial-clases.svg` (17 líneas), archivos sueltos que no correspondían al formato pedido por la consigna (Excalidraw).
- Se eliminó `01-boceto_inicial_clases.png`, que era un PNG casi duplicado del archivo principal (RC9).
- Se modificó `01-boceto-inicial.excalidraw` y se regeneró `01-boceto-inicial.png`.

**Verificación de contenido:** se extrajeron las etiquetas de texto del `.excalidraw` corregido. Se confirmó que:
- La clase `Pedido` ahora tiene `prioridad: Boolean` (antes era `Integer`, un tipo incorrecto para un campo binario).
- Aparecen las clases `Usuario`, `Personalizacion`, `RegistroAuditoria` y `Combo`, que antes faltaban pese a estar descriptas en el README y en los casos de uso.
- Ya no aparecen las clases `Cliente` ni `Local`, que estaban fuera de alcance del MVP (el negocio no registra clientes ni administra múltiples locales en esta etapa).

**Veredicto:** Aprobado. El fix es coherente con los requisitos y casos de uso documentados en `introduccion.md`.

## Code Review 2 — PR #25 "fix: actualizar modelo de dominio (RC19)" y PR #26 "fix: corregir documentación RC22-RC25" (autora: @neith18)
**Revisión:** Se compararon los diffs de `anexos/introduccion.md` en ambos merges contra su base.
- PR #25 corrigió la sección "7. Modelo de dominio inicial", quitando `Local` y `Cliente` de la lista de entidades, para que coincida con el diagrama de clases ya corregido en PR #22.
- PR #26 sumó sobre ese mismo texto la imagen embebida `![Boceto inicial de clases](../diagramas/01-diagrama-clases/01-boceto-inicial.png)`, que antes solo estaba enlazada como archivo fuente `.excalidraw` sin previsualización.

**Verificación de contenido:** el texto resultante de `introduccion.md` (sección 7) es consistente con la lista de clases verificada en el Code Review 1 (`Usuario, Pedido, ItemPedido, Producto, Combo, Personalizacion, Comanda, Pago, RegistroAuditoria, EstadoPedido`), sin duplicar ni contradecir el diagrama.

**Veredicto:** Aprobado. Ambos fixes son coherentes entre sí y con el diagrama de clases corregido.

## Pendiente
La consigna pide un mínimo de 4 code reviews asistidas con IA sobre PRs de otros integrantes. Al momento de este documento solo existen 2 PRs de otros integrantes con contenido sustancial para revisar de forma genuina (además de las de estructura/naming, que no requieren una revisión de coherencia funcional). Las 2 revisiones restantes se completarán sobre las Pull Requests de Tarjetas CRC y Diagramas de Casos de Uso de la Actividad Obligatoria N°2 en cuanto los responsables de esos roles las abran, siguiendo la misma metodología descripta arriba.
