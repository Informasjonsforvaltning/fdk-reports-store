## FDK reports store

This repository contains GitHub Actions workflows for deploying an elasticsearch instance using a shared Helm chart from the [`helm-chart`](https://github.com/Informasjonsforvaltning/helm-chart) repository.

## Purpose

The main goal of this repository is to manage environment-specific elasticsearch deployments (staging, demo & prod) for the FDK ecosystem using reusable Helm charts. <br>
All configuration and logic for deployment resides in GitHub Actions, while the Helm chart itself is maintained in a centralized location.

> [!Note]
> This repository is not intended for direct use. It is a wrapper around the Helm chart repository and is designed to be used in conjunction with it.

## Repository Structure

```
.
├── .github/
    └── workflows/
        ├── deploy-staging.yaml       # GitHub Actions workflow to deploy elasticsearch to staging
        └── deploy-prod&demo.yaml     # GitHub Actions workflow to deploy elasticsearch to prod & demo
```

## Deployment

The deployment is triggered via GitHub Actions when changes are pushed to the repository or by manual triggers.
For running one of the workflows, navigate to the `Actions` tab in the GitHub repository and select the desired workflow (`Deploy to staging` or `Deploy to production & demo`).

Secrets required for deployment (e.g., GCP service account keys) are stored as GitHub secrets in the repository settings.

## Helm Chart Source

The elasticsearch Helm chart used in this repository is maintained in:

🔗 [`Informasjonsforvaltning/helm-chart`](https://github.com/Informasjonsforvaltning/helm-chart/helm-chart-sources/fdk-reports-store)

Any updates or changes to the elasticsearch configuration must be done there.

## Requirements

- Access to GitHub Actions.
- Required secrets configured.

## Updating the Chart Version

The workflows will automatically pull the latest version of the chart in the helm-chart repo and deploy it to the specified environment.
