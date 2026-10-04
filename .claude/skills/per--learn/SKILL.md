# Skill: per--learn

Añade uno o varios aprendizajes a `architect/assets/learnings.md` (o a un fichero temático de `architect/assets/learnings/`) del proyecto.

## Trigger

Usar cuando el usuario invoque `/per--learn` o pida guardar un aprendizaje, corrección o patrón a recordar.

## Instrucciones

### 1. Localizar el framework

Las rutas son relativas a la raíz del proyecto: `architect/assets/learnings.md` y `architect/assets/learnings/`. Si `architect/` no existe, informa que el Architect Framework no está instalado (`sys--template-pull architect` + `architect/INIT.md`) y detente.

### 2. Determinar el aprendizaje

Si el usuario pasó texto como argumento al invocar el skill (ej. `/per--learn nunca usar X porque Y`), úsalo como punto de partida.

Si no hay argumento, pregunta al usuario qué aprendizaje quiere guardar.

### 2b. Determinar destino

Lee `architect/assets/learnings/_index.md`. Si el fichero no existe aún, el destino es `architect/assets/learnings.md` directamente — omite este paso.

Pregunta al usuario: "¿Es un learning transversal (va a `architect/assets/learnings.md`) o específico de una temática?"

- **Transversal** → destino = `architect/assets/learnings.md`. Continúa al paso 3.
- **Temático** → muestra la tabla del índice y pregunta qué fichero usar. El usuario elige uno existente o escribe un nombre nuevo.
  - Si es un fichero nuevo:
    1. Pide al usuario: temas que cubre y en qué contexto cargarlo (una línea cada uno).
    2. Crea `architect/assets/learnings/<nombre>.md` con cabecera mínima:
       ```markdown
       # Learnings — <Nombre del tema>
       ```
    3. Añade una fila en la tabla de `_index.md` con Fichero, Temas y Cuándo cargar.
  - Destino = `architect/assets/learnings/<nombre>.md`

### 3. Estructurar el aprendizaje

Para cada aprendizaje, obtén o infiere los tres campos del formato de `learnings.md`:

- **Contexto**: qué se estaba haciendo cuando surgió el aprendizaje
- **Feedback/Error**: qué salió mal o qué corrigió el usuario (o qué funcionó bien y debe repetirse)
- **Regla**: qué hacer (o no hacer) en el futuro — formulado como regla aplicable

Si el usuario proporcionó texto libre, infiere los tres campos tú mismo y muéstraselos para que los confirme o corrija antes de guardar.

Si falta información clave para algún campo, pregunta solo lo necesario — no hagas más de una ronda de preguntas.

### 4. Escribir en learnings.md

Lee `architect/assets/learnings.md` y añade al final cada aprendizaje con este formato:

```markdown
## YYYY-MM-DD — [tema en 3-6 palabras]
**Contexto**: [qué se estaba haciendo]
**Feedback**: [qué salió mal o qué corrigió el usuario]
**Regla**: [qué hacer o no hacer en el futuro]
```

Usa la fecha actual. Si hay varios aprendizajes, añádelos todos en el mismo paso.

### 5. Confirmar

Informa al usuario de cuántas entradas se añadieron y muestra el texto final de cada una tal como quedó en el archivo.

## Notas

- NUNCA sobreescribas entradas existentes — solo añade al final.
- Si el usuario quiere corregir el texto antes de guardar, permítele hacerlo.
- Un aprendizaje puede ser positivo (patrón a repetir) o negativo (error a evitar) — el campo **Feedback** debe reflejarlo.
