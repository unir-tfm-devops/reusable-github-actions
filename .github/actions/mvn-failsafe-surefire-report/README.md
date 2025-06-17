# mvn-failsafe-surefire-report

Composite GitHub action to publish Maven Failsafe and Surefire test reports as a comment to a pull request.

### Action inputs

| Input                  | Description                                                                                                    | Default value                                                                 | Required |
|------------------------|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|----------|
| initial-comment-message| Initial text for the comment posted on the PR                                                                  | See action.yml                                                                | false    |
| comment-message        | Message appended to the comment posted on the PR. Supports templating for test results.                        | See action.yml                                                                | false    |
| unit-tests-title       | The title of unit tests report                                                                                  | Unit tests report                                                             | false    |
| integration-tests-title| The title of integration tests report                                                                           | Integration tests report                                                      | false    |

### Example of usage:

```yaml
name: 'Maven Test Reports Example'

on:
  pull_request:
    branches:
      - main

jobs:
  test-report:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Publish Maven Test Reports
        uses: unir-tfm-devops/reusable-github-actions/.github/actions/mvn-failsafe-surefire-report@main
```