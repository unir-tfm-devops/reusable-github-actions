# Reusable GitHub Actions & Workflows

This repository contains a collection of reusable GitHub Actions and Workflows designed to streamline CI/CD processes, infrastructure management, and development workflows for the organization.

## 📋 Table of Contents

- [Overview](#overview)
- [Reusable Actions](#reusable-actions)
- [Reusable Workflows](#reusable-workflows)
- [Usage Examples](#usage-examples)
- [Requirements](#requirements)
- [Contributing](#contributing)

## 🎯 Overview

This repository provides standardized, reusable components for:
- **CI/CD Pipelines**: Automated testing, building, and deployment workflows
- **Infrastructure Management**: Terraform workflows for AWS and Azure
- **Container Management**: Docker build and push operations
- **Helm Chart Management**: Chart packaging and publishing
- **Java/Maven Development**: Setup and testing utilities
- **Version Management**: Automated version updates across repositories

## 🔧 Reusable Actions

### Maven Setup (`mvn-setup`)
Configures Java and Maven environment for Java-based projects. See [action README](.github/actions/mvn-setup/README.md) for detailed usage.

### Docker Build & Push (`docker-build-push`)
Builds Docker images and pushes them to Amazon ECR. See [action README](.github/actions/docker-build-push/README.md) for detailed usage.

### Helm Package & Push (`helm-package-push`)
Packages Helm charts and pushes them to ChartMuseum repository. See [action README](.github/actions/helm-package-push/README.md) for detailed usage.

### Version Updater (`version-updater`)
Updates application versions in workloads repositories for ArgoCD deployment. See [action README](.github/actions/version-updater/README.md) for detailed usage.

### Maven Test Reports (`mvn-failsafe-surefire-report`)
Publishes Maven test reports (Surefire and Failsafe) as comments on pull requests. See [action README](.github/actions/mvn-failsafe-surefire-report/README.md) for detailed usage.

## 🔄 Reusable Workflows

### Spring Boot CI/CD Workflows
Specialized workflows for Spring Boot applications:
- `ci-cd-release.yml`: Release pipeline for Spring Boot apps
- `ci-cd-pr.yml`: PR pipeline for Spring Boot apps
- `ci-cd-non-release.yml`: Non-release pipeline for Spring Boot apps

### Node.js CI/CD Workflows
Specialized workflows for Node.js applications:
- `ci-cd-release-nodejs.yml`: Release pipeline for Node.js apps
- `ci-cd-pr-nodejs.yml`: PR pipeline for Node.js apps
- `ci-cd-non-release-nodejs.yml`: Non-release pipeline for Node.js apps

### Terraform Workflows
Infrastructure management workflows supporting AWS and Azure:
- `terraform-apply.yml`: Applies Terraform configurations to cloud infrastructure
- `terraform-plan.yml`: Creates Terraform execution plans for review
- `terraform-destroy.yml`: Destroys Terraform-managed infrastructure

### PR Checks (`pr-checks.yml`)
Standard pull request validation workflow.

## 🔑 Requirements

### Secrets Required
- `AWS_ACCESS_KEY`: AWS access key ID
- `AWS_SECRET_KEY`: AWS secret access key
- `AZURE_CLIENT_ID`: Azure client ID
- `AZURE_CLIENT_SECRET`: Azure client secret
- `AZURE_TENANT_ID`: Azure tenant ID
- `AZURE_SUBSCRIPTION_ID`: Azure subscription ID
- `UNIR_TFM_APP_PRIVATE_KEY`: GitHub App private key

### Variables Required
- `UNIR_TFM_APP_ID`: GitHub App ID

### Permissions
- Repository access for GitHub App
- Cloud provider credentials (AWS/Azure)
- ChartMuseum repository access (for Helm charts)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Adding New Actions
- Place new actions in `.github/actions/`
- Include comprehensive documentation
- Add usage examples
- Update this README

### Adding New Workflows
- Place new workflows in `.github/workflows/`
- Make them reusable with `workflow_call` trigger
- Document all inputs and outputs
- Update this README

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
