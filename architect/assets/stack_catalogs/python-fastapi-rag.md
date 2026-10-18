# Stack — Python / FastAPI / RAG sobre PostgreSQL

Backend Python con FastAPI, PostgreSQL + pgvector, Docker Compose y despliegue en EC2. Extraído de `BMAD_test5` (AECC Tech Transfer Assistant).

## Componentes

| Componente | En este stack | Cuándo cargar |
|------------|---------------|---------------|
| [python.md](../IT_components/python.md) | Poetry, entorno de desarrollo Python | Cuando la sesión trate dependencias, `poetry` o `pip` |
| [postgresql.md](../IT_components/postgresql.md) | PostgreSQL 16 + pgvector (HNSW), SQLAlchemy 2.0 async, Alembic | Cuando la sesión trate configuración, rendimiento o conexiones de PostgreSQL |
| [docker.md](../IT_components/docker.md) | Docker Compose: `db`, `app`, nginx y Certbot | Cuando la sesión trate construcción, despliegue o pin de versiones de imágenes |
| [aws.md](../IT_components/aws.md) | EC2, EBS, S3 (backups), SES, SSM | Cuando la sesión trate cuotas, límites de servicio o comportamiento de S3/SSM |

**Instrucción de carga automática**: cuando la sesión trate alguno de los temas de la tabla, usa `Read` sobre `architect/assets/IT_components/<fichero>` antes de responder por primera vez. Informa: "He cargado IT_components/<fichero> para esta sesión."

## Notas del stack

- Capas del proyecto de origen: FastAPI + uvicorn, SQLAlchemy 2.0 async, Alembic, psycopg 3, LiteLLM, Langfuse, nginx como proxy reverso con TLS vía Certbot.
- Tooling de test E2E con Playwright (Node) separado de la app Python. Sin componente propio todavía.
