# Azure Pipelines Configuration

This folder contains the Azure Pipelines YAML file (`azure-pipelines.yml`) for building and deploying a containerized application using Azure services.

## Pipeline Overview

The pipeline is triggered on every push to the `main` branch and consists of three main stages:

### 1. Build

- **Builds and pushes a Docker image** to the specified Azure Container Registry.
- Tags the image with the build ID and as `latest`.
- Adds a custom build tag with the last scanned date.

### 2. Deploy to Development

- **Deploys the built Docker image** to the development Azure Container App.
- Uses Azure CLI to update the container app with the new image.

### 3. Deploy to Production

- **Deploys the same Docker image** to the production Azure Container App.
- Runs only after a successful deployment to development.
- Uses Azure CLI to update the production container app.

## Variables

- **imageRepository:** Name of the image repository in ACR.
- **containerRegistry:** Service connection for ACR.
- **containerRegistryName:** Name of the Azure Container Registry.
- **dockerfilePath:** Path to the Dockerfile.
- **tag:** Tag for the Docker image (uses the build ID).
- **azureSubscriptionDev/Prd:** Azure service connections for dev/prod.
- **resourceGroupDev/Prd:** Resource group names for dev/prod.
- **containerAppNameDev/Prd:** Container App names for dev/prod.

## How It Works

1. **Build Stage:**  
   Builds the Docker image and pushes it to ACR with two tags: the build ID and `latest`.

2. **DeployToDev Stage:**  
   Updates the development Container App to use the new image.

3. **DeployToProd Stage:**  
   Updates the production Container App to use the same image, after successful deployment to development.

## Customization

- Set the variable values in the pipeline or Azure DevOps UI to match your environment.
- Ensure service connections and resource names are configured in Azure DevOps.

## Requirements

- Azure DevOps project with pipeline permissions.
- Azure Container Registry and Container Apps set up.
- Service connections for Azure subscriptions.

```// filepath: /workspace/.azure/README.md

# Azure Pipelines Configuration

This folder contains the Azure Pipelines YAML file (`azure-pipelines.yml`) for building and deploying a containerized application using Azure services.

## Pipeline Overview

The pipeline is triggered on every push to the `main` branch and consists of three main stages:

### 1. Build

- **Builds and pushes a Docker image** to the specified Azure Container Registry.
- Tags the image with the build ID and as `latest`.
- Adds a custom build tag with the last scanned date.

### 2. Deploy to Development

- **Deploys the built Docker image** to the development Azure Container App.
- Uses Azure CLI to update the container app with the new image.

### 3. Deploy to Production

- **Deploys the same Docker image** to the production Azure Container App.
- Runs only after a successful deployment to development.
- Uses Azure CLI to update the production container app.

## Variables

- **imageRepository:** Name of the image repository in ACR.
- **containerRegistry:** Service connection for ACR.
- **containerRegistryName:** Name of the Azure Container Registry.
- **dockerfilePath:** Path to the Dockerfile.
- **tag:** Tag for the Docker image (uses the build ID).
- **azureSubscriptionDev/Prd:** Azure service connections for dev/prod.
- **resourceGroupDev/Prd:** Resource group names for dev/prod.
- **containerAppNameDev/Prd:** Container App names for dev/prod.

## How It Works

1. **Build Stage:**  
   Builds the Docker image and pushes it to ACR with two tags: the build ID and `latest`.

2. **DeployToDev Stage:**  
   Updates the development Container App to use the new image.

3. **DeployToProd Stage:**  
   Updates the production Container App to use the same image, after successful deployment to development.

## Customization

- Set the variable values in the pipeline or Azure DevOps UI to match your environment.
- Ensure service connections and resource names are configured in Azure DevOps.

## Requirements

- Azure DevOps project with pipeline permissions.
- Azure Container Registry and Container Apps set up.
- Service connections for