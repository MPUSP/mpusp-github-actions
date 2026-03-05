
# MPUSP GitHub Actions

This repository contains reusable GitHub Actions workflows for the [MPUSP](https://www.mpusp.mpg.de/), the Max Planck Unit for the Science of Pathogens.

## Overview

These workflows are designed to streamline CI processes across MPUSP projects by providing standardized, reusable automation templates.
Their main purpose is to secure a harmonized, easy-to-maintain, and up-to-date collection of reusable CI workflows for our [Snakemake pipelines](https://github.com/orgs/MPUSP/repositories).

## Usage

To use these workflows in your repository, reference them in your workflow files:

```yaml
jobs:
    my-job:
        uses: mpusp/mpusp-github-actions/.github/workflows/workflow-name.yml@main
```

## Workflows

Documentation for individual workflows coming soon.

## Contributing

For issues and comments, please leave an issue on [Github](https://github.com/MPUSP/mpusp-github-actions/issues).
For further questions, please contact bioinformatics@mpusp.mpg.de.
