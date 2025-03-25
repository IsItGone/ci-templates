# CI Templates

Reusable GitHub Actions workflows for CI/CD pipelines across multiple repositories.

## 📦 Features

- Standardized workflows for build, test, Docker image publishing, and Helm chart deployment
- Environment-based deployment logic (e.g., dev for `main`, prod for `release*`)
- Reusable via `workflow_call`

## 🚀 Usage

To reuse a workflow from this repository in another repo:

```yaml
jobs:
  docker:
    uses: IsItGone/ci-templates/.github/workflows/docker-build-push.yml@main
    with:
      version-tag: 1.0.0
      hash-tag: 3DFA14B      
```

## 📁 Available Workflows

| Workflow                                | Description                                         |
|-----------------------------------------|-----------------------------------------------------|
| `.github/workflows/docker-build-push.yml` | Docker build & push using GitHub Container Registry |
| `.github/workflows/java-gradle-build.yml` | Java + Gradle build                                 |
| `.github/workflows/helm-deploy.yml`       | Helm chart repository update & deployment           |
