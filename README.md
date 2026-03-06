# MPUSP GitHub Actions

This repository contains reusable GitHub Actions workflows for the [MPUSP](https://www.mpusp.mpg.de/), the Max Planck Unit for the Science of Pathogens.

## Overview

These workflows are designed to streamline CI processes across MPUSP projects by providing standardized, reusable automation templates.
Their main purpose is to secure a harmonized, easy-to-maintain, and up-to-date collection of reusable CI workflows for our [Snakemake pipelines](https://github.com/orgs/MPUSP/repositories).

## Workflows

Currently available workflows include:

- `snakemake-tests`: Runs standardized tests for Snakemake workflows.
- `deploy-apptainer`: Builds and deploys Apptainer containers for Snakemake workflows to GitHub Packages ([GHCR](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)). **Note**: work in progress, use carefully!
- `release-please`: Automates the release process using the [release-please](https://github.com/googleapis/release-please) tool.
- `conventional-prs`: Lints pull requests for conventional commit messages.

## Usage

To use these workflows in your repository, reference them in your workflow files as outlined below.
Note: workflows can be pinned to a specific version tag (`@v1.0`), but it is recommended to use the latest stable version (`@main`) in order to keep manual intervention in workflows to a minimum.

### Snakemake Tests

```yaml
name: Snakemake Tests

on:
  pull_request:
    branches: [main]

jobs:
  snakemake-tests:
    uses: MPUSP/mpusp-github-actions/.github/workflows/snakemake-tests.yml@main
    with:
      cores: 2
      dryrun: false
```

### Deploy Apptainer

```yaml
name: Deploy Apptainer

on:
  workflow_run:
    workflows: ["Release Please"]
    types:
      - completed
  workflow_dispatch:

permissions:
  contents: read
  packages: write

jobs:
  deploy-apptainer:
    if: ${{ github.event_name == 'workflow_dispatch' || github.event.workflow_run.conclusion == 'success' }}
    uses: MPUSP/mpusp-github-actions/.github/workflows/deploy-apptainer.yml@main
```

### Release Please

```yaml
name: Release Please

on:
  push:
    branches: [main]

permissions:
  contents: write
  pull-requests: write
  issues: write

jobs:
  release-please:
    uses: MPUSP/mpusp-github-actions/.github/workflows/release-please.yml@main
```

### Conventional PRs

```yaml
name: Conventional PRs

on:
  pull_request_target:
    types:
      - opened
      - reopened
      - edited
      - synchronize

permissions:
  pull-requests: read

jobs:
  conventional-prs:
    uses: MPUSP/mpusp-github-actions/.github/workflows/conventional-prs.yml@main
```

## Contributing

For issues and comments, please leave an issue on [Github](https://github.com/MPUSP/mpusp-github-actions/issues).
For further questions, please contact bioinformatics@mpusp.mpg.de.

## Authors

- MPUSP bioinformatics team (http://mpusp.github.io/)
