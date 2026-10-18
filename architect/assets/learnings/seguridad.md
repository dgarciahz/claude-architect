# Learnings — Seguridad (secretos, credenciales, .env, git)

## 2026-09-24 — No subir ficheros con claves a repos
**Contexto**: configurando `.env` de BMAD_test5 con claves de OpenAI/Anthropic para el contenedor Docker.
**Feedback**: el usuario preguntó si es seguro poner API keys en `.env`; se verificó que estaba en `.gitignore` y sin trackear, pero pidió dejar la regla explícita para el futuro.
**Regla**: ficheros con claves/secretos NUNCA se suben a un repo público; en repo privado solo se suben con confirmación FUERTE y explícita del usuario (no vale un "ok" genérico a un `git add`/`commit` amplio) — verificar siempre `.gitignore` antes de cualquier `git add`/`commit` que pueda incluirlos.

## 2026-10-18 — .gitignore no protege lo ya trackeado
**Contexto**: `claude-research-skills`: `starter/` y `.claude/` acababan en GitHub (23 ficheros trackeados) pese a estar en `.gitignore`; el paso 7 de `sys--template-pull` hace `git add` de esas rutas.
**Feedback**: la causa se buscó primero en el `.gitignore`, pero este solo afecta a ficheros sin trackear.
**Regla**: ante "se commitea algo ignorado", mirar `git ls-files` antes que el `.gitignore`. Si ya está en el índice, sacarlo con `git rm -r --cached` y revisar qué paso del flujo hace el `git add`.
