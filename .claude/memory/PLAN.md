# PLAN.md

Plan maestro vigente. Cuando el plan cambie, edita aquí y registra el cambio en `PROGRESS.md`.

## Objetivo actual

Implantar un sistema de memoria persistente para que Claude Code recuerde, entre sesiones, qué se ha hecho en cada proyecto y cuál es el plan vigente.

## Estado

En curso — sistema base recién creado en la rama `claude/code-memory-persistence-UOQyF`.

## Próximos pasos

- [x] Crear `CLAUDE.md` con las reglas de memoria.
- [x] Crear esqueleto en `.claude/memory/` (PROJECT, PLAN, PROGRESS, DECISIONS).
- [x] Configurar hook `SessionStart` en `.claude/settings.json` que vuelque la memoria al inicio.
- [ ] Validar el hook en una nueva sesión (al volver, confirmar que el resumen aparece).
- [ ] Poblar `PROGRESS.md` con la bitácora real del proyecto cuando se retomen tareas de la guía.
- [ ] (Opcional) Añadir el mismo sistema a otros repos del usuario, una vez probado aquí.

## Fuera de alcance por ahora

- Sincronización de memoria entre repos distintos.
- Compresión/resumen automático de `PROGRESS.md` cuando crezca.
- Edición del contenido de la guía (`README.md`, `Themes/`).
