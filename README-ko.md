# CI Templates

이 리포지토리는 여러 리포지토리에서 재사용할 수 있는 GitHub Actions composite actions를 제공합니다.

## 📦 기능

- 빌드, 테스트, Docker 이미지 빌드 및 푸시를 위한 표준화된 composite actions 제공
- Gradle 기반 JAR 빌드와 Docker Buildx를 활용한 이미지 빌드 및 푸시 지원

## 🚀 사용법

다른 리포지토리에서 이 리포지토리의 composite action을 사용하려면, 워크플로우 파일 내에서 아래와 같이 참조하세요.  
최신 액션을 사용하려면 항상 main ref(@main)를 참조하시기 바랍니다.

예를 들어, Gradle JAR 빌드를 수행하려면 다음 예시와 같이 참조합니다:
```yaml
uses: IsItGone/ci-templates@main/.github/actions/build-jar@main
```

Docker 이미지 빌드 및 푸시를 수행하려면 다음 예시와 같이 참조합니다:  
```yaml
uses: IsItGone/ci-templates@main/.github/actions/build-and-push-image@main
with:  
  tag: 1.0.0  
  image-name: owner/image  
  password: ${{ secrets.DOCKER_PASSWORD }}
```
## 📁 사용 가능한 Composite Actions

| Action 경로                                          | 설명                                             |
| ---------------------------------------------------- | ------------------------------------------------ |
| .github/actions/build-jar                            | Gradle 기반 JAR 빌드                              |
| .github/actions/build-and-push-image                 | Docker Buildx를 사용한 이미지 빌드 및 푸시          |

## 🔧 Action 입력값 상세

### build-jar 액션
- 이 액션은 Gradle 기반 JAR 빌드를 수행합니다.
- 위의 예시와 같이 참조하면 되며, 별도의 입력값은 없습니다.

### build-and-push-image 액션
이 액션은 Docker Buildx를 사용하여 Docker 이미지를 빌드하고 푸시합니다. 입력값은 아래와 같이 정의되어 있습니다.

| 입력값      | 설명                              | 필수 여부 | 기본값          |
|-------------|-----------------------------------|-----------|-----------------|
| dockerfile  | Dockerfile의 경로                 | ❌        | "./Dockerfile"  |
| tag         | 이미지 태그 (커밋 해시 또는 버전)   | ✔️        | -               |
| image-name  | 이미지 이름 (형식: owner/image)     | ✔️        | -               |
| registry    | Docker registry                   | ❌        | "ghcr.io"       |
| username    | Docker username                   | ❌        | "ddd-cute-bot"  |
| password    | Docker password                   | ✔️        | -               |

이 composite action을 사용할 때는 필수 입력값(tag, image-name, password)을 반드시 제공해야 하며, 선택 입력값은 기본값으로도 사용 가능합니다.
