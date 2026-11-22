# Mysthos CI/CD Templates

Workflows reutilizables de GitHub Actions para los proyectos de **Mysthos** (Docker + Trivy + GHCR + Auto-Deploy por SSH).

## Uso en cualquier repositorio

Crea `.github/workflows/ci-cd.yml` en el repo destino:

```yaml
name: CI/CD + Trivy

on:
  push:
    branches: [ "master" ]
  workflow_dispatch:

permissions:
  contents: read
  packages: write
  security-events: write

jobs:
  pipeline:
    uses: devarkoru/mysthos-ci-templates/.github/workflows/docker-trivy-deploy.yml@main
    with:
      compose_dir: ~/torneos_e2e
      compose_files: "-f docker-compose.yml -f docker-compose.prod.yml"
      service_name: frontend
    secrets: inherit
```
