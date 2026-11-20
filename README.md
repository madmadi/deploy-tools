# deploy-tools

Reusable GitHub Actions workflows for deploying small projects to a VPS.

## Workflows

- `deploy-docker-image.yml` — build a Docker image on GitHub Actions, ship it to a VPS, and restart a Docker Compose stack. Pass `service_name` when the Compose service and the image name differ (used by the rollback capture).
- `deploy-flutter-web.yml` — build a Flutter web app on the runner and rsync `build/web` to a VPS directory, with optional `--dart-define` and a public health check.
- `deploy-rsync-remote.yml` — rsync source to a VPS and run a remote command (build + restart service, or `docker-compose up --build`, etc.).

## Required GitHub secrets per project

- `SSH_PRIVATE_KEY`
- `HOST`
- `USER` — must have passwordless sudo for `docker`, `docker-compose`, and any service commands the workflow runs.

## Usage

Pin callers to a release tag (e.g. `@v1.1.0`) rather than `@main` to avoid surprise changes:

```yaml
jobs:
  deploy:
    uses: madmadi/deploy-tools/.github/workflows/deploy-docker-image.yml@v1.1.0
    # ...
```
