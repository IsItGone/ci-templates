# CI Templates

이 리포지토리는 여러 리포지토리에서 재사용할 수 있는 GitHub Actions composite actions를 제공합니다.

## 📦 Features

- 표준화된 composite actions를 통한 빌드, 테스트, Docker 이미지 빌드 및 푸시 기능 제공
- Gradle 기반 JAR 빌드와 Docker Buildx를 활용한 이미지 빌드 및 푸시 지원

## 🚀 Usage

리포지토리 내 composite action을 다른 리포지토리에서 사용하려면 아래와 같이 워크플로우 파일 내에서 참조할 수 있습니다.

### 예시: Gradle JAR 빌드

```yaml
jobs:
  build-jar:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build JAR with Gradle
        uses: IsItGone/ci-templates/.github/actions/build-jar/action.yaml
```

### 예시: Docker 이미지 빌드 및 푸시

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

📁 사용 가능한 Composite Actions

| Action Path                                      | 설명                                               |
| ------------------------------------------------ | -------------------------------------------------- |
| .github/actions/build-jar/action.yaml            | Gradle 기반 JAR 빌드                                |
| .github/actions/build-and-push-image/action.yaml | Docker Buildx를 사용한 이미지 빌드 및 푸시           |
