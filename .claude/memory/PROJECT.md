# PROJECT.md

Contexto estable del proyecto. Actualiza este archivo solo cuando cambien hechos fundamentales (stack, propósito, estructura).

## Qué es

**The Windows 11 Start menu styling guide** — guía de referencia para personalizar visualmente el menú Inicio de Windows 11 mediante el mod de Windhawk "Windows 11 Start Menu Styler".

Audiencia: usuarios técnicos que quieren crear o adaptar temas para el menú Inicio.

## Stack

- Documentación principal en Markdown (`README.md`).
- Temas distribuidos como conjuntos de reglas XAML/CSS-like en carpetas bajo `Themes/`, cada una con su propio `README.md` y capturas.
- No hay código compilable; el repo es contenido + configuración.

## Estructura del repositorio

```
.
├── README.md               # Guía principal (índice en el encabezado)
├── Themes/                 # Temas de ejemplo, uno por carpeta
│   └── <NombreTema>/
│       ├── README.md
│       └── *.png / *.xaml
├── CLAUDE.md               # Instrucciones para Claude Code
└── .claude/
    ├── settings.json       # Hooks y permisos
    └── memory/             # Memoria persistente entre sesiones
        ├── PROJECT.md
        ├── PLAN.md
        ├── PROGRESS.md
        └── DECISIONS.md
```

## Convenciones

- Idioma del repo: inglés (README, nombres de archivo).
- Idioma de la memoria interna (`.claude/memory/`): español, porque es la lengua de trabajo con el usuario.
- Capturas de pantalla en PNG dentro de la carpeta del tema correspondiente.
- Rama de desarrollo activa: `claude/code-memory-persistence-UOQyF`.

## Enlaces externos

- Windhawk: https://windhawk.net
- Mod del Start Menu Styler: ver `README.md` para enlace canónico.
