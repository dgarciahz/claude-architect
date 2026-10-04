# Architect Framework — Inicialización

Instrucciones para inicializar el Architect Framework en el proyecto actual. Es autocontenido e idempotente: puede ejecutarse varias veces.

El framework aporta conocimiento de arquitectura transversal (no ligado a un usuario): `architect/assets/learnings.md`, `architect/assets/learnings/` y `architect/assets/IT_stacks/`, más los skills `/per--learn` y `/per--stack`, que escriben directamente en esos ficheros. La fuente de verdad es el repo `claude-architect`; lo que se añada en un proyecto se propaga con `sys--template-push architect`.

## Cómo invocar

- `"ejecuta architect/INIT.md"`
- `"inicializa el architect framework"`

---

## Instrucciones de inicialización

### Paso 1 — Verificar estructura

Comprueba que existen `architect/assets/learnings.md`, `architect/assets/learnings/_index.md` y `architect/assets/IT_stacks/_index_stacks.md`. Si falta alguno, el pull del template está incompleto: informa y detente. NUNCA los recrees vacíos.

### Paso 2 — Actualizar CLAUDE.md (obligatorio)

Los ficheros de arquitectura se cargan desde `architect/assets/`, no desde `CLAUDE_PERSONAL_DIR`. Este paso es lo que hace que el framework tenga efecto: no lo omitas.

Lee `CLAUDE.md` en la raíz (si no existe, créalo con la cabecera `# CLAUDE.md`).

**2.1 — Bloque ARCHITECT**: si existe `<!-- ARCHITECT:START -->`, reemplaza el bloque completo hasta `<!-- ARCHITECT:END -->`. Si no existe, añádelo al final:

```
<!-- ARCHITECT:START — no eliminar este bloque -->
@architect/assets/learnings.md
@architect/assets/learnings/_index.md
@architect/assets/IT_stacks/_index_stacks.md
<!-- ARCHITECT:END -->
```

**2.2 — Migración**: si `CLAUDE.md` tiene un bloque `<!-- PERSONALIZATION:START -->` con imports de `learnings.md`, `learnings/_index.md` o `IT_stacks/_index_stacks.md` apuntando a `CLAUDE_PERSONAL_DIR`, elimina solo esas líneas (dejan de ser la fuente). No toques `soul.md` ni `user.md`.

### Paso 3 — Migrar datos previos (solo si aplica)

Si en `$CLAUDE_PERSONAL_DIR` (de `.claude/settings.local.json#env`) existen `learnings.md`, `learnings/` o `IT_stacks/` con contenido que no está en `architect/assets/`, no lo sobrescribas ni lo borres: lista las diferencias y pregunta al usuario si fusionarlas en `architect/assets/`.

### Paso 4 — Commit

Modo template (`git remote get-url origin` contiene `dgarciahz/claude-architect`): `CLAUDE.md` sigue gitignoreado, no lo incluyas.

Modo derivado:

```bash
git add CLAUDE.md architect/
git commit -m "Inicializa proyecto desde architect framework — <fecha>"
```

### Paso 5 — Confirmar al usuario

Informa de: bloque ARCHITECT añadido/actualizado, líneas migradas de PERSONALIZATION, diferencias detectadas en `CLAUDE_PERSONAL_DIR`, y que hay que reiniciar Claude Code para cargar los imports.

---

## Notas

- Re-ejecutar aplica cambios del template sin perder contenido.
- Para desinstalar: elimina el bloque ARCHITECT de `CLAUDE.md` y el directorio `architect/`.
