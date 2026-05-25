# PROGRESS.md

Bitácora cronológica. Entrada nueva al cerrar cada tarea significativa. No borrar entradas previas.

Formato:
```
## YYYY-MM-DD — Título breve
- Qué se hizo
- Por qué
- Archivos clave tocados
```

---

## 2026-05-25 — Sistema de memoria persistente inicial

- Creado `CLAUDE.md` con reglas para Claude sobre cómo usar y mantener la memoria.
- Creado directorio `.claude/memory/` con cuatro archivos base: `PROJECT.md`, `PLAN.md`, `PROGRESS.md`, `DECISIONS.md`.
- Configurado hook `SessionStart` en `.claude/settings.json` para volcar la memoria al inicio de cada sesión.
- Motivo: en sesiones previas el usuario pidió un resumen del plan maestro y Claude respondió que no había, porque la conversación no persiste entre sesiones y nada estaba commiteado.
- Archivos tocados: `CLAUDE.md`, `.claude/memory/*.md`, `.claude/settings.json`.

## 2026-05-25 — Regla de confirmación para actualizar memoria

- Endurecida la regla 3 de `CLAUDE.md`: ahora Claude debe preguntar explícitamente antes de escribir o commitear entradas de memoria al cerrar un hito.
- Incluye una formulación sugerida ("Cerramos el hito X. ¿Actualizo la memoria?...") y enumeración de qué cuenta como hito cerrado.
- Motivo: petición del usuario para evitar actualizaciones automáticas que pasen desapercibidas y mantener al usuario en el bucle de decisión.
- Archivos tocados: `CLAUDE.md`.
