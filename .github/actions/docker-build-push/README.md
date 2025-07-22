# Docker Build & Push Action

This reusable GitHub Action builds a Docker image and pushes it to either Azure Container Registry (ACR) or Amazon ECR based on the specified cloud provider.

## Inputs

### Required Inputs

- `cloud-provider`: Cloud provider to push to (`aws` or `azure`)
- `image-repo-name`: The name of the repository to push the Docker image to
- `image-tag`: The tag for the Docker image

### Azure-specific Inputs (required when `cloud-provider` is `azure`)

- `azure-client-id`: Azure Client ID
- `azure-client-secret`: Azure Client Secret

### AWS-specific Inputs (required when `cloud-provider` is `aws`)

- `aws-access-key`: AWS Access Key ID
- `aws-secret-key`: AWS Secret Access Key

## Usage Examples

### For Azure Container Registry (ACR)

```yaml
- name: Build and push to ACR
  uses: ./.github/actions/docker-build-push
  with:
    cloud-provider: 'azure'
    image-repo-name: 'my-app'
    image-tag: 'v1.0.0'
    azure-client-id: ${{ secrets.AZURE_CLIENT_ID }}
    azure-client-secret: ${{ secrets.AZURE_CLIENT_SECRET }}
```

### For Amazon ECR

```yaml
- name: Build and push to ECR
  uses: ./.github/actions/docker-build-push
  with:
    cloud-provider: 'aws'
    image-repo-name: 'my-app'
    image-tag: 'v1.0.0'
    aws-access-key: ${{ secrets.AWS_ACCESS_KEY_ID }}
    aws-secret-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

## Notes

- The action automatically handles authentication for the specified cloud provider
- For AWS ECR, the action uses the AWS ECR login action to get the registry URL dynamically
- For Azure ACR, the action uses the default login server `unirtfmdevops.azurecr.io`
- The Docker build context is assumed to be the current directory (`.`)
- Make sure you have the necessary secrets configured in your GitHub repository
- The action uses a unified approach for building image tags, reducing code duplication