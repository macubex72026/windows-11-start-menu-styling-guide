# DECISIONS.md

Decisiones de diseño relevantes y su justificación. No editar entradas pasadas: si se revierte una decisión, añadir una nueva entrada que lo explique.

Formato:
```
## YYYY-MM-DD — Título de la decisión
**Contexto**: …
**Decisión**: …
**Alternativas consideradas**: …
**Consecuencias**: …
```

---

## 2026-05-25 — Memoria persistente como archivos versionados en `.claude/memory/`

**Contexto**: Claude Code on the web ejecuta cada sesión en un contenedor efímero. El historial de conversación no sobrevive al cierre de sesión ni a la compactación de contexto.

**Decisión**: Guardar la memoria del proyecto como Markdown en `.claude/memory/`, commitearla en cada cambio, y cargarla automáticamente al inicio con un hook `SessionStart`.

**Alternativas consideradas**:
- Solo `CLAUDE.md` en la raíz (auto-cargado): se queda corto cuando el proyecto crece; un solo archivo mezcla contexto estable y bitácora.
- Memoria externa (base de datos, servicio): añade dependencia, no sobrevive al entorno efímero sin red, complica el setup.
- `/remember` ad-hoc: útil para hechos sueltos, no para un plan estructurado.

**Consecuencias**:
- La memoria viaja con el repo: cualquier clon (o nuevo contenedor) la tiene.
- Es revisable en PRs como cualquier otro archivo.
- Requiere disciplina: Claude debe actualizar los archivos al cerrar tareas (regla obligatoria en `CLAUDE.md`).

## 2026-05-25 — Actualización de memoria requiere confirmación del usuario

**Contexto**: La regla 3 inicial de `CLAUDE.md` indicaba que Claude actualizara la memoria automáticamente al cerrar un hito. Eso deja al usuario fuera del bucle: las entradas pueden mezclar lo importante con lo trivial, redactarse de forma imprecisa, o registrar como "hecho" algo que el usuario aún no considera cerrado.

**Decisión**: Antes de escribir o commitear cualquier entrada en `PROGRESS.md`, `DECISIONS.md` o `PLAN.md`, Claude debe preguntar explícitamente al usuario, indicando qué archivos tocaría y un resumen de la entrada propuesta. Solo tras confirmación se escribe y commitea.

**Alternativas consideradas**:
- Actualización automática (regla original): rápida, pero opaca y propensa a inflar la bitácora con cosas irrelevantes.
- Actualización solo bajo orden explícita ("actualiza la memoria"): obliga al usuario a recordarlo; los hitos pasan sin registrarse.
- Pregunta proactiva (elegida): Claude detecta el cierre del hito y pide permiso; el usuario decide en el momento, sin tener que acordarse.

**Consecuencias**:
- El usuario mantiene control editorial sobre la memoria.
- Claude debe ser razonable detectando "hito cerrado" sin preguntar en cada cambio trivial (criterios listados en `CLAUDE.md`).
- Pequeño coste de fricción: una pregunta extra al cerrar hitos. Aceptable a cambio del control.
