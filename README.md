# Docker GHCR Action

This GitHub Action builds and pushes Docker images to the GitHub Container Registry.

## Inputs

- `registry`: Docker registry to use (default: `ghcr.io`)
- `username`: Username for the Docker registry
- `password`: Password or token for the Docker registry
- `image_name`: Name of the Docker image
- `dockerfile`: Path to the Dockerfile (default: `Dockerfile`)

## Example Usage

```yaml
uses: your-username/docker-ghcr-action@v1
with:
  username: ${{ secrets.DOCKER_USERNAME }}
  password: ${{ secrets.DOCKER_PASSWORD }}
  image_name: my-image
