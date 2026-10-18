# IT Components — Índice de Ficheros

Catálogo de docs por componente (plataforma/herramienta/entorno). Actualizar al crear un nuevo fichero en `IT_components/`.

| Fichero | Plataformas / herramientas | Cuándo cargar |
|---------|---------------------------|---------------|
| [windows.md](windows.md) | Windows, Git Bash, SSL, schannel, line endings, paths, bash | Cuando la sesión implique setup o configuración en entorno Windows |
| [llmwiki.md](llmwiki.md) | llmwiki, llm-wiki-compiler, OKF wiki compiler | Cuando la sesión trate configuración, límites o coste de `llmwiki`/`llm-wiki-compiler` |
| [aws.md](aws.md) | AWS, Lambda, MemorySize, cuotas de cuenta, CloudFormation, S3, SSM | Cuando la sesión trate cuotas, límites de servicio, soporte AWS o comportamiento de CloudFormation/S3/SSM |
| [lightrag.md](lightrag.md) | LightRAG, RAG, grafo de conocimiento, pgvector, workspace, PGTableGraphStorage, Apache AGE, MCP server, embeddings | Cuando la sesión trate configuración, storage, despliegue o arquitectura de LightRAG |
| [docker.md](docker.md) | Docker, Compose, buildx, registries, pin de versiones, digests | Cuando la sesión trate construcción, despliegue o pin de versiones de imágenes Docker |
| [postgresql.md](postgresql.md) | PostgreSQL, PgBouncer, conexiones, pooling, max_connections | Cuando la sesión trate configuración, rendimiento o despliegue de PostgreSQL |
| [n8n.md](n8n.md) | n8n, workflows, MCP server de n8n, Chat Trigger, Webhook | Cuando la sesión trate creación o edición de workflows n8n o su uso vía MCP |

**Instrucción de carga automática**: cuando la sesión trate setup o configuración de alguna de las plataformas de la tabla, usa `Read` para cargar el fichero de componente antes de responder por primera vez. Informa: "He cargado IT_components/<fichero>.md para esta sesión."

**Para añadir o actualizar entradas**: usa el skill `/arch--it_component`. Gestiona deduplicación y evita contradicciones.
