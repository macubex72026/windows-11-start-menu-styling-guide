# CLAUDE.md

Guía para Claude Code en este repositorio. Este archivo se carga automáticamente al inicio de cada sesión.

## Sistema de memoria persistente

Este proyecto usa archivos de memoria versionados en `.claude/memory/`. Son la **fuente de verdad** sobre el estado del proyecto entre sesiones, porque la conversación no persiste.

### Archivos de memoria

| Archivo | Propósito |
|---|---|
| `.claude/memory/PROJECT.md` | Qué es el proyecto, stack, convenciones, estructura |
| `.claude/memory/PLAN.md` | Plan maestro actual y próximos pasos |
| `.claude/memory/PROGRESS.md` | Bitácora cronológica de lo que se ha hecho |
| `.claude/memory/DECISIONS.md` | Decisiones de diseño con su justificación |

### Reglas obligatorias para Claude

1. **Al inicio de cada sesión**: leer los cuatro archivos de `.claude/memory/` antes de proponer cambios o responder sobre el alcance/estado del proyecto. El hook `SessionStart` ya los muestra, pero verifica leyéndolos.

2. **Si el usuario pregunta por el plan, el progreso, o "qué hemos hecho"**: la respuesta sale de estos archivos. Si no hay información, dilo explícitamente — no inventes.

3. **Al cerrar un hito o tarea significativa**: actualizar el archivo correspondiente y commitearlo en el mismo cambio. No dejes la memoria desincronizada con el código.
   - Cambio de código → entrada nueva en `PROGRESS.md` con fecha (YYYY-MM-DD)
   - Decisión de diseño → entrada en `DECISIONS.md`
   - Cambio de alcance o nuevos pasos → actualizar `PLAN.md`

4. **Formato de entradas en `PROGRESS.md`**:
   ```
   ## YYYY-MM-DD — Título breve
   - Qué se hizo
   - Por qué
   - Archivos clave tocados
   ```

5. **No borrar entradas antiguas de `PROGRESS.md` ni de `DECISIONS.md`** — son historial. Si una decisión se revierte, añade una nueva entrada que lo explique, no edites la vieja.

6. **Commitea la memoria** junto con el código que la genera. Este entorno (Claude Code on the web) es efímero: lo que no esté en git, no existe en la próxima sesión.

## Sobre el proyecto

Guía de estilos para el menú Inicio de Windows 11, basada en Windhawk. Detalles completos en `.claude/memory/PROJECT.md`.

Estructura:
- `README.md` — la guía pública
- `Themes/` — temas de ejemplo (uno por carpeta, con su propio README)
- `.claude/memory/` — memoria persistente del proyecto
- `.claude/settings.json` — configuración del harness, incluido el hook `SessionStart`

## Convenciones

- No modificar archivos en `Themes/` salvo petición explícita: son artefactos publicados.
- Cambios al `README.md`: mantener el formato del índice y la numeración de secciones.
- Commits descriptivos en imperativo. No mencionar el modelo ni la sesión en el mensaje.

## Rama de trabajo

Desarrollo en `claude/code-memory-persistence-UOQyF` salvo indicación contraria.
