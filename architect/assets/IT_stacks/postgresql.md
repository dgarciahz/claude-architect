# IT Stack — PostgreSQL

## Conexiones

Postgres crea un proceso (fork) por conexión, no un thread. Ráfagas de conexiones nuevas (rapid fire) saturan CPU/memoria por el coste de fork y pueden colapsar el servidor antes de llegar a `max_connections`. Poner PgBouncer delante: reutiliza un pool reducido de conexiones reales y absorbe la ráfaga.
