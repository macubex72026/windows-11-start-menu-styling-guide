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
