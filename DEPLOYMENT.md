# Deployment

This project uses Poetry for dependency management and Docker Compose for deployment.

Poetry virtual environments are disabled in the Docker image with:

```bash
POETRY_VIRTUALENVS_CREATE=false
```

Build and run locally:

```bash
docker compose up --build -d
```

Run on the server:

```bash
docker compose up --build -d
```

The application is exposed on port `8000` by default and runs with `DJANGO_DEBUG=1` so Django serves static files for the practical task requirements.

To use another host port locally:

```bash
APP_PORT=18000 docker compose up --build -d
```
