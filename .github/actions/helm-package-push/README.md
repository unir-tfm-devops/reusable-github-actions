# helm-package-push

Composite GitHub action for packaging a Helm chart and pushing it to a ChartMuseum repository.

### Action inputs

| Input            | Description                                              | Default value | Required |
|------------------|----------------------------------------------------------|---------------|----------|
| helm-path        | The path to the Helm chart directory                     | helm          | false    |
| chart-version    | The version of the Helm chart to package                 | n/a           | true     |
| chartmuseum-url  | The URL of the ChartMuseum repository                    | n/a           | true     |

### Example of usage:

```yaml
name: 'Helm Package & Push example'

on:
  push:
    branches:
      - main

jobs:
  helm-package-push:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Helm Package & Push
        uses: unir-tfm-devops/reusable-github-actions/.github/actions/helm-package-push@main
        with:
          helm-path: ./charts/mychart
          chart-version: 1.2.3
          chartmuseum-url: https://chartmuseum.example.com
```