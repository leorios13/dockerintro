## Emerson Service

Tech stack: Python + Flask

This service exposes an HTTP API on port 8080.

Endpoints:

- `/` returns the message identifying the student and neighborhood.
- `/health` returns a health status.

Every request to `/` logs a message into:

/var/log/app/visitas.log

This file will be stored in the shared Docker volume
"La Biblioteca del Pueblo".
