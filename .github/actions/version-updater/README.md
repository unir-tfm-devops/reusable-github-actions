# version-updater

Composite GitHub action for updating the version of an application in the workloads repository to deploy the service using ArgoCD.

### Action inputs

| Input        | Description                                              | Default value | Required |
|--------------|----------------------------------------------------------|---------------|----------|
| version      | Version to update in the workloads repository            | n/a           | true     |
| app-name     | Name of the application to update                        | n/a           | true     |
| environment  | Environment where the application is deployed             | test          | false    |
| cloud        | Cloud provider (aws or azure)                            | aws           | false    |
| app-id       | GitHub App ID                                            | n/a           | true     |
| private-key  | GitHub App private key                                   | n/a           | true     |

### Example of usage:

```yaml
name: 'Version Update Example'

on:
  push:
    tags:
      - 'v*'

jobs:
  update-version:
    runs-on: ubuntu-latest
    steps:
      - name: Update Application Version
        uses: unir-tfm-devops/reusable-github-actions/.github/actions/version-updater@main
        with:
          version: ${{ github.ref_name }}
          app-name: my-application
          environment: production
          cloud: aws
          app-id: ${{ vars.UNIR_TFM_APP_ID }}
          private-key: ${{ secrets.UNIR_TFM_APP_PRIVATE_KEY }}
```

### What this action does:

1. **Determines Repository**: Based on the cloud provider (aws/azure), it selects the appropriate workloads repository (eks-workloads/aks-workloads)
2. **Authenticates**: Uses GitHub App credentials to authenticate with the workloads repository
3. **Updates Chart.yaml**: Updates the dependency version in the application's Chart.yaml file
4. **Updates values.yaml**: Updates the image tag in the application's values.yaml file
5. **Commits Changes**: Automatically commits and pushes the changes to the workloads repository

### Prerequisites:

- GitHub App with access to the workloads repository
- The application must exist in the workloads repository under `environments/{environment}/applications/{app-name}/`
- The workloads repository must have the expected structure with Chart.yaml and values.yaml files 