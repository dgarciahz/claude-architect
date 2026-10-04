# Architect Framework — Inicialización

Instrucciones para inicializar el Architect Framework en el proyecto actual. Idempotente: puede ejecutarse varias veces.

El framework se instala con `/sys--template-pull architect`, que copia `architect/` y los skills `per--learn` y `per--stack` a `.claude/skills/`. INIT.md no instala nada: comprueba los skills y conecta el contenido a `CLAUDE.md`.

## Cómo invocar

- `"ejecuta architect/INIT.md"`
- `"inicializa el architect framework"`

---

## Instrucciones de inicialización

### Paso 1 — Verificar skills y contenido

Comprueba que existen `.claude/skills/per--learn/SKILL.md` y `.claude/skills/per--stack/SKILL.md`, y los ficheros `architect/assets/learnings/learnings.md`, `architect/assets/learnings/_index.md` y `architect/assets/IT_stacks/_index_stacks.md`.

Si falta alguno: informa de cuáles y de que hay que ejecutar `/sys--template-pull architect`; detente. NUNCA los recrees vacíos.

### Paso 2 — Bloque ARCHITECT en CLAUDE.md (obligatorio)

Los ficheros de arquitectura se cargan desde `architect/assets/`. Sin este paso el framework no tiene efecto: no lo omitas.

Lee `CLAUDE.md` en la raíz (si no existe, créalo con la cabecera `# CLAUDE.md`).

Si existe `<!-- ARCHITECT:START -->`, reemplaza el bloque completo hasta `<!-- ARCHITECT:END -->`. Si no existe, añádelo al final:

```
<!-- ARCHITECT:START — no eliminar este bloque -->
@architect/assets/learnings/learnings.md
@architect/assets/learnings/_index.md
@architect/assets/IT_stacks/_index_stacks.md
<!-- ARCHITECT:END -->
```

### Paso 3 — Quitar referencias antiguas de PERSONALIZATION

Si `CLAUDE.md` tiene un bloque `<!-- PERSONALIZATION:START -->` con líneas `@.../learnings.md`, `@.../learnings/_index.md` o `@.../IT_stacks/_index_stacks.md` (apuntando a `CLAUDE_PERSONAL_DIR`), elimina solo esas líneas. No toques `soul.md` ni `user.md`.

### Paso 4 — Confirmar al usuario

Informa de: skills verificados, bloque ARCHITECT añadido/actualizado, líneas eliminadas de PERSONALIZATION, y que hay que reiniciar Claude Code para cargar los imports.

---

## Notas

- Re-ejecutar aplica cambios del template sin perder contenido.
- Para desinstalar: elimina el bloque ARCHITECT de `CLAUDE.md`, el directorio `architect/` y los skills `per--learn` y `per--stack`.
