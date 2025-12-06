# Py-reusable-workflows

Reusable GitHub Actions workflows for Azure deployments - Python/Django variant.

## Available Workflows

### Infrastructure

| Workflow | Description |
|----------|-------------|
| `setup-azure-infrastructure.yml` | Creates/verifies Resource Group and App Service Plan |
| `setup-app-infrastructure.yml` | Creates Web App, Database (PostgreSQL/MySQL), Storage Account |
| `destroy-app-infrastructure.yml` | Destroys app-specific resources |

### Deployment

| Workflow | Description |
|----------|-------------|
| `spinup-destroy.yml` | Preview environment manager (create/destroy on PR labels) |
| `deploy-production.yml` | Production deployment workflow |
| `deploy-staging.yml` | Staging deployment workflow |

### Build

| Workflow | Description |
|----------|-------------|
| `build.yml` | Generic build workflow |
| `docker-build-python.yml` | Docker build for Python apps |
| `docker-build-js-ts.yml` | Docker build for JS/TS apps |

### Testing & Linting

| Workflow | Description |
|----------|-------------|
| `test.yml` | Test runner workflow |
| `lint.yml` | Linting workflow |
| `pr_checks.yml` | PR validation checks |
| `push_checks.yml` | Push validation checks |

## Usage

Reference these workflows from your repository:

```yaml
jobs:
  deploy:
    uses: Kuniqo/Py-reusable-workflows/.github/workflows/deploy-production.yml@main
    with:
      app-name: 'my-app'
      docker-image-name: 'ghcr.io/org/app:tag'
      # ... other inputs
    secrets:
      AZURE_CREDENTIALS: ${{ secrets.AZURE_CREDENTIALS }}
      # ... other secrets
```

## Features

- PostgreSQL and MySQL support
- Azure Storage Account with sync from existing storage
- Prisma migrations support
- Preview environments with PR labels
- Modular architecture for easy customization

## License

MIT
