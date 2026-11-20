# deploy-tools

Reusable GitHub Actions workflows for deploying small projects to a VPS.

## Workflows

- `deploy-docker-image.yml` — build a Docker image on GitHub Actions, ship it to a VPS, and restart a Docker Compose stack.
- `deploy-rsync-remote.yml` — rsync source to a VPS and run a remote command (build + restart service, or `docker-compose up --build`, etc.).

## Required GitHub secrets per project

- `SSH_PRIVATE_KEY`
- `HOST`
- `USER`
