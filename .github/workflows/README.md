# Frontend Container Build and Deploy Pipeline

This folder contains a GitHub Actions workflow (`github-actions.yml`) that automates building, pushing, and deploying a frontend container image to Azure.

## Workflow Overview

The workflow is triggered on every push to the `main` branch. It performs the following steps:

1. **Build and Push Docker Image**
   - Checks out the repository code.
   - Logs in to Azure Container Registry (ACR).
   - Builds the Docker image for the frontend.
   - Tags the image with a version and as `latest`.
   - Pushes both tags to ACR.

2. **Deploy to Development Environment**
   - Logs in to Azure.
   - Deploys the newly built image to the development Azure Web App.
   - Logs out of Azure.

3. **Deploy to UAT Environment**
   - Waits for successful deployment to development.
   - Logs in to Azure.
   - Deploys the image to the UAT Azure Web App.
   - Logs out of Azure.

4. **Deploy to Production Environment**
   - Waits for successful deployment to UAT.
   - Logs in to Azure.
   - Deploys the image to the production Azure Web App.
   - Logs out of Azure.

## Environment Variables

- **ACR_REGISTRY:** Azure Container Registry server address.
- **FRONTEND_IMAGE:** Docker image name for the frontend.
- **VERSION:** Version tag for the image, based on repository variables and the GitHub run number.
- **DEV_APP_NAME, UAT_APP_NAME, PRD_APP_NAME:** Azure Web App names for each environment.

## Secrets and Variables

- **Secrets:** Used for authentication with Azure and ACR (e.g., `AZURE_CLIENT_ID`, `AZURE_TENANT_ID`, `AZURE_SUBSCRIPTION_ID`, `ACR_REGISTRY_USERNAME`, `ACR_REGISTRY_PASSWORD`).
- **Variables:** Used for image naming and versioning.

## Notes

- Each deployment step depends on the previous one to ensure sequential promotion from development to production.
- The workflow uses official Azure GitHub Actions for authentication and deployment.
- Customize the environment variable values and secrets in your repository settings as needed.

```// filepath: /workspace/.github/workflows/README.md

# Frontend Container Build and Deploy Pipeline

This folder contains a GitHub Actions workflow (`github-actions.yml`) that automates building, pushing, and deploying a frontend container image to Azure.

## Workflow Overview

The workflow is triggered on every push to the `main` branch. It performs the following steps:

1. **Build and Push Docker Image**
   - Checks out the repository code.
   - Logs in to Azure Container Registry (ACR).
   - Builds the Docker image for the frontend.
   - Tags the image with a version and as `latest`.
   - Pushes both tags to ACR.

2. **Deploy to Development Environment**
   - Logs in to Azure.
   - Deploys the newly built image to the development Azure Web App.
   - Logs out of Azure.

3. **Deploy to UAT Environment**
   - Waits for successful deployment to development.
   - Logs in to Azure.
   - Deploys the image to the UAT Azure Web App.
   - Logs out of Azure.

4. **Deploy to Production Environment**
   - Waits for successful deployment to UAT.
   - Logs in to Azure.
   - Deploys the image to the production Azure Web App.
   - Logs out of Azure.

## Environment Variables

- **ACR_REGISTRY:** Azure Container Registry server address.
- **FRONTEND_IMAGE:** Docker image name for the frontend.
- **VERSION:** Version tag for the image, based on repository variables and the GitHub run number.
- **DEV_APP_NAME, UAT_APP_NAME, PRD_APP_NAME:** Azure Web App names for each environment.

## Secrets and Variables

- **Secrets:** Used for authentication with Azure and ACR (e.g., `AZURE_CLIENT_ID`, `AZURE_TENANT_ID`, `AZURE_SUBSCRIPTION_ID`, `ACR_REGISTRY_USERNAME`, `ACR_REGISTRY_PASSWORD`).
- **Variables:** Used for image naming and versioning.

## Notes

- Each deployment step depends on the previous one to ensure sequential promotion from development to production.
- The workflow uses official Azure GitHub Actions for authentication and deployment.
- Customize the environment variable values and secrets in