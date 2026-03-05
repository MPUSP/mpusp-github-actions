# MPUSP GitHub Actions

This repository contains reusable GitHub Actions workflows for the [MPUSP](https://www.mpusp.mpg.de/), the Max Planck Unit for the Science of Pathogens.

## Overview

These workflows are designed to streamline CI processes across MPUSP projects by providing standardized, reusable automation templates.
Their main purpose is to secure a harmonized, easy-to-maintain, and up-to-date collection of reusable CI workflows for our [Snakemake pipelines](https://github.com/orgs/MPUSP/repositories).

## Usage

To use these workflows in your repository, reference them in your workflow files like this (example for `release-please`):

```yaml
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

It is possible to optionally give it a `name:`, otherwise the name from the called workflow is used.

## Workflows

Currently available workflows include:

- `snakemake-tests`: Runs standardized tests for Snakemake workflows.
- `deploy-apptainer`: Builds and deploys Apptainer containers for Snakemake workflows to GitHub Packages ([GHCR](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)). **Note**: work in progress, use carefully!
- `release-please`: Automates the release process using the [release-please](https://github.com/googleapis/release-please) tool.
- `conventional-prs`: Lints pull requests for conventional commit messages.

## Contributing

For issues and comments, please leave an issue on [Github](https://github.com/MPUSP/mpusp-github-actions/issues).
For further questions, please contact bioinformatics@mpusp.mpg.de.
