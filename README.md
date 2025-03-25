# CI Templates

This repository provides reusable GitHub Actions composite actions for CI/CD pipelines across multiple repositories.

## 📦 Features

- Standardized composite actions for build, test, Docker image build, and push
- Supports Gradle-based JAR build and Docker Buildx for building and pushing images

## 🚀 Usage

To use a composite action from this repository in another repository, reference it in your workflow file as shown below.

### Example: Gradle JAR Build

```yaml
jobs:
  build-jar:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build JAR with Gradle
        uses: IsItGone/ci-templates/.github/actions/build-jar/action.yaml
```

### Example: Docker Image Build and Push
```yaml
jobs:
  docker:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build and Push Docker Image
        uses: IsItGone/ci-templates/.github/actions/build-and-push-image/action.yaml
        with:
          tag: 1.0.0
          image-name: owner/image
          password: ${{ secrets.DOCKER_PASSWORD }}
          # Optional inputs:
          # dockerfile: "./Dockerfile"
          # registry: "ghcr.io"
          # username: "ddd-cute-bot"
```

📁 Available Composite Actions

| Action Path                                      | Description                                        |
| ------------------------------------------------ | -------------------------------------------------- |
| .github/actions/build-jar/action.yaml            | Gradle-based JAR build                             |
| .github/actions/build-and-push-image/action.yaml | Docker Buildx for building and pushing images      |

