# Architect Framework — Inicialización

Instrucciones para inicializar el Architect Framework en el proyecto actual. Idempotente: puede ejecutarse varias veces.

El framework se instala con `/core--template-pull architect`, que copia `architect/` y los skills `arch--learn` y `arch--it_component` a `.claude/skills/`. INIT.md no instala nada: comprueba los skills y conecta el contenido a `CLAUDE.md`.

## Cómo invocar

- `"ejecuta architect/INIT.md"`
- `"inicializa el architect framework"`

---

## Instrucciones de inicialización

### Paso 1 — Verificar skills y contenido

Comprueba que existen `.claude/skills/arch--learn/SKILL.md` y `.claude/skills/arch--it_component/SKILL.md`, y los ficheros `architect/assets/learnings/learnings.md`, `architect/assets/learnings/_index.md` y `architect/assets/IT_components/_index_components.md`.

Si falta alguno: informa de cuáles y de que hay que ejecutar `/core--template-pull architect`; detente. NUNCA los recrees vacíos.

### Paso 2 — Elegir stack(s)

Los componentes (`architect/assets/IT_components/`) se agrupan en catálogos de stack (`architect/assets/stack_catalogs/*.md`). Un proyecto importa solo los catálogos que usa; así `CLAUDE.md` no anuncia componentes que no le corresponden.

1. Lista `architect/assets/stack_catalogs/*.md`: nombre del fichero y primera línea de descripción (la que sigue al título).
2. Si `CLAUDE.md` ya tiene un bloque ARCHITECT con líneas `@architect/assets/stack_catalogs/...`, esa es la selección actual: muéstrala y pregunta si se mantiene o se cambia. Por defecto se mantiene.
3. Si no hay selección previa, pregunta con `AskUserQuestion` (multiSelect, un catálogo por opción) qué stacks usa el proyecto. Un proyecto puede elegir varios, por ejemplo un stack de aplicación y uno de máquina de desarrollo.
4. Si el usuario no elige ninguno, no responde o pide "todo", se mantiene el comportamiento completo: se importa `_index_components.md`, que anuncia todos los componentes.

### Paso 2b — Bloque ARCHITECT en CLAUDE.md (obligatorio)

Los ficheros de arquitectura se cargan desde `architect/assets/`. Sin este paso el framework no tiene efecto: no lo omitas.

Lee `CLAUDE.md` en la raíz (si no existe, créalo con la cabecera `# CLAUDE.md`).

Si existe `<!-- ARCHITECT:START -->`, reemplaza el bloque completo hasta `<!-- ARCHITECT:END -->`. Si no existe, añádelo al final. Contenido según el paso 2:

Con stacks elegidos (una línea por catálogo; no se importa `_index_components.md`):

```
<!-- ARCHITECT:START — no eliminar este bloque -->
@architect/assets/learnings/learnings.md
@architect/assets/learnings/_index.md
@architect/assets/stack_catalogs/<catalogo>.md
<!-- ARCHITECT:END -->
```

Sin stack elegido (todo):

```
<!-- ARCHITECT:START — no eliminar este bloque -->
@architect/assets/learnings/learnings.md
@architect/assets/learnings/_index.md
@architect/assets/IT_components/_index_components.md
<!-- ARCHITECT:END -->
```

### Paso 3 — Quitar referencias antiguas de PERSONALIZATION

Si `CLAUDE.md` tiene un bloque `<!-- PERSONALIZATION:START -->` con líneas `@.../learnings.md`, `@.../learnings/_index.md` o `@.../IT_components/_index_components.md` (apuntando a `CLAUDE_PERSONAL_DIR`), elimina solo esas líneas. No toques `soul.md` ni `user.md`.

### Paso 4 — Registrar hook de versión en settings.json

Lee `.claude/settings.json` (si no existe, tratarlo como `{}`). Comprueba si ya existe una entrada en `hooks.SessionStart[].hooks[]` con `"command": "bash architect/assets/version-check.sh"`.

- **Sí existe** → omitir.
- **No existe** → añadir al array `hooks.SessionStart[]` la siguiente entrada, preservando todas las entradas existentes:

```json
{
  "hooks": [
    {
      "type": "command",
      "command": "bash architect/assets/version-check.sh"
    }
  ]
}
```

Escribir `.claude/settings.json` resultante.

### Paso 5 — Confirmar al usuario

Informa de: skills verificados, stacks elegidos (o "todo"), bloque ARCHITECT añadido/actualizado, líneas eliminadas de PERSONALIZATION, hook de versión (añadido | ya existía), y que hay que reiniciar Claude Code para cargar los imports.

---

## Notas

- Re-ejecutar aplica cambios del template sin perder contenido. La selección de stacks vive en el bloque ARCHITECT de `CLAUDE.md`, que `core--template-pull` no toca.
- Para desinstalar: elimina el bloque ARCHITECT de `CLAUDE.md`, el directorio `architect/` y los skills `arch--learn` y `arch--it_component`.
