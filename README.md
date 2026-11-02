# Komodo Git Deploy Test

## Project Overview

This project explores Git-based Docker builds and automated deployment through Komodo.

The application is a simple HTML website served by Nginx inside a Docker container.

## Current Setup

- **Application:** Hello World webpage.
- **Docker:** Builds the application image.
- **Docker Compose:** Runs the application container.
- **GitHub Actions:** Validates, builds and tests the Docker image.
- **Komodo:** Planned Git-based deployment integration.
- **Container Registry:** Awaiting confirmation of the approved registry.

## Run Locally

Make sure Docker Desktop is running.

Validate the Compose configuration:

```bash
docker compose config --quiet
```

Build and start the application:

```bash
docker compose up -d --build
```

Open the application:

http://localhost:19192

Check the container:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs -f
```

Stop the application:

```bash
docker compose down
```

## GitHub Actions

Workflow location:

`.github/workflows/docker-ci.yml`

The workflow:
1. Checks out the repository.
2. Validates Docker Compose configuration.
3. Builds the Docker image.
4. Starts a temporary container.
5. Verifies the webpage response and expected content.

## Current Status

- Local Docker build passed.
- Local container test passed.
- GitHub Actions workflow passed.

## Planned Improvements

- Connect an approved container registry.
- Configure Docker image publishing.
- Integrate Git-based deployment through Komodo.
- Confirm the secrets-management approach.
- Test deployment on Unraid.
- Explore Slack deployment and error notifications.

## Security

- Never commit passwords, API tokens or private keys.
- Never commit unencrypted environment files.
- Use the approved secrets-management approach for deployment.