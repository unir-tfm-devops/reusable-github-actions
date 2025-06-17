# mvn-setup

Composite GitHub action for setting up Maven and Java for building a Java artifact.

### Action inputs

| Input             | Description                                              | Default value | Required |
|-------------------|----------------------------------------------------------|---------------|----------|
| java-version      | The Java version to set up                               | 24            | false    |
| java-distribution | The Java distribution to set up                          | temurin       | false    |
| maven-version     | The Maven version to set up                              | 3.9.6         | false    |
| maven-cache       | Set up Maven cache                                       | true          | false    |

### Example of usage:

```yaml
name: 'Maven example'

on:
  pull_request:
    branches:
      - main

jobs:
  build-test:
    name: Application build & test
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Maven & Java
        uses: unir-tfm-devops/reusable-github-actions/.github/actions/mvn-setup@main
        with:
          java-version: 21
          java-distribution: temurin
          maven-version: 3.9.6
          maven-cache: true

      - name: Unit tests
        run: mvn clean test

      - name: Integration tests
        run: mvn clean verify

      - name: Package
        run: mvn clean package -DskipTests=true
``` 