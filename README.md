# Docker GHCR Action

## Description

The **Docker GHCR Action** is a GitHub Action designed to build and push Docker images to the GitHub Container Registry (GHCR). It automates the process of Docker image creation and deployment, allowing seamless integration into your CI/CD workflows.

## Inputs

- **registry** (optional):  
  *Description*: Docker registry to use.  
  *Default*: `ghcr.io`

- **username** (required):  
  *Description*: Username for the Docker registry.

- **password** (required):  
  *Description*: Password or token for the Docker registry.

- **image_name** (required):  
  *Description*: Name of the Docker image.

- **dockerfile** (optional):  
  *Description*: Path to the Dockerfile.  
  *Default*: `Dockerfile`

- **context** (optional):  
  *Description*: Context path for the Docker build.  
  *Default*: `.`

- **env_text** (optional):  
  *Description*: Environment variables as text.

- **build_args** (optional):  
  *Description*: Build arguments for Docker.

- **npmrc_content** (optional):  
  *Description*: Contents of the `.npmrc` file.

## Permissions

- **contents**: read
- **packages**: write

## Usage

To use this action in your GitHub workflow, include it in your `.github/workflows/your-workflow-file.yml`:

```yaml
name: Build and Push Docker Image

on:
  push:
    branches:
      - main

jobs:
  build-and-push:
    runs-on: ubuntu-latest
    steps:
      - name: Use Docker GHCR Action
        uses: your-repo/docker-ghcr-action@v1
        with:
          username: ${{ secrets.GHCR_USERNAME }}
          password: ${{ secrets.GHCR_TOKEN }}
          image_name: your-image-name
          # Optionally override defaults
          dockerfile: path/to/Dockerfile
          context: path/to/context
          env_text: |
            VAR1=value1
            VAR2=value2
          build_args: ARG1=value1,ARG2=value2
          npmrc_content: |
            registry=https://registry.npmjs.org/
