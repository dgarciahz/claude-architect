# Skill: arch--stack

Añade o actualiza entradas en los stack docs de `architect/assets/IT_components/`.

## Trigger

Usar cuando el usuario invoque `/arch--stack [texto]` o pida "añadir al stack", "actualizar stack", "guardar en stack", etc.

## Instrucciones

### 1. Localizar el framework

Las rutas son relativas a la raíz del proyecto: `architect/assets/IT_components/`. Si `architect/` no existe, informa que el Architect Framework no está instalado (`sys--template-pull architect` + `architect/INIT.md`) y detente.

### 2. Identificar stack file

Lee `architect/assets/IT_components/_index_components.md`. Determina a qué fichero pertenece la nueva info. Si no es obvio, muestra la tabla al usuario y pregunta.

### 3. Leer el stack file

Lee el fichero completo.

### 4. Check de deduplicación

Busca contenido similar o contradictorio en la sección relevante:

- Si hay solapamiento sin contradicción → informa y pregunta si actualizar o añadir igualmente.
- Si hay contradicción → muestra ambas versiones y pregunta qué mantener.
- Si no hay solapamiento → continúa.

### 5. Identificar sección de destino

Determina a qué sección (`##`) del stack file pertenece la nueva info. Si no existe la sección, créala.

### 6. Escribir

Añade la entrada en la sección correspondiente. Formato: prosa concisa, sin fecha, sin campos Contexto/Feedback/Regla (eso es para learnings). Si se actualiza una entrada existente en lugar de añadir, reemplaza solo esa línea/bloque.

### 7. Confirmar

Muestra el bloque añadido/modificado tal como quedó en el fichero.

## Notas

- NUNCA sobreescribas una sección entera — solo la entrada afectada.
- Si el usuario quiere crear un stack file nuevo (nueva plataforma): crea el `.md` en `IT_components/` con cabecera y secciones iniciales, y añade la fila correspondiente en `_index_components.md`.
