# docker-build-push

Composite GitHub action for building a Docker image and pushing it to Amazon ECR.

### Action inputs

| Input           | Description                                              | Default value | Required |
|-----------------|----------------------------------------------------------|---------------|----------|
| image-repo-name | The name of the ECR repository to push the Docker image to| n/a           | true     |
| image-tag       | The tag for the Docker image                             | n/a           | true     |
| aws-access-key  | AWS Access Key ID                                        | n/a           | true     |
| aws-secret-key  | AWS Secret Access Key                                    | n/a           | true     |

### Example of usage:

```yaml
name: 'Docker Build & Push Example'

on:
  push:
    branches:
      - main

jobs:
  docker-build-push:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Build & Push Docker Image
        uses: unir-tfm-devops/reusable-github-actions/.github/actions/docker-build-push@main
        with:
          image-repo-name: my-ecr-repo
          image-tag: latest
          aws-access-key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```