# IT Component — Python

## Poetry

Poetry no resuelve `pypi.org` en el entorno sandboxed de `BMAD_test5`: `poetry lock` falla con "All attempts to connect to pypi.org failed". `pip` y `npm` sí funcionan en el mismo entorno, así que es un problema específico del resolver de Poetry. Confirmado en dos sesiones distintas. Regenerar `poetry.lock` desde una máquina con red real, y dejar diferidas las dependencias que obliguen a relockear (por ejemplo `pytest-cov`).
