# CI Templates

This repository offers reusable GitHub Actions composite actions for use across multiple repositories.

## 📦 Features

- Standardized composite actions for building, testing, and for Docker image build & push.
- Supports Gradle-based JAR builds and Docker image build & push using Docker Buildx.

## 🚀 Usage

To integrate the composite actions defined in this repository into your workflow, reference them in your workflow file. It is recommended to use the main ref (e.g., @main) to always obtain the latest version of the actions.

For instance, to perform a Gradle JAR build, use like:  
```yaml
uses: IsItGone/ci-templates@main/.github/actions/build-jar
```

For Docker image build and push, use like:  
```yaml
uses: IsItGone/ci-templates@main/.github/actions/build-and-push-image  
with:  
  tag: 1.0.0  
  image-name: owner/image  
  password: ${{ secrets.DOCKER_PASSWORD }}  
  # Optional inputs:  
  # dockerfile: "./Dockerfile"  
  # registry: "ghcr.io"  
  # username: "ddd-cute-bot"
```
## 📁 Available Composite Actions

| Action Path                                         | Description                                       |
| --------------------------------------------------- | ------------------------------------------------- |
| .github/actions/build-jar                           | Gradle-based JAR build                            |
| .github/actions/build-and-push-image                | Docker image build and push using Docker Buildx   |

## 🔧 Action Input Details

### build-jar Action
- This action performs a Gradle-based JAR build.
- Reference it as shown above. (There are no additional inputs for this action.)

### build-and-push-image Action
This action builds and pushes a Docker image using Docker Buildx. The inputs are defined as follows:

| Input       | Description                                  | Required | Default         |
|-------------|----------------------------------------------|----------|-----------------|
| dockerfile  | Path to the Dockerfile                       | ❌       | "./Dockerfile"  |
| tag         | Image tag (commit hash or version)           | ✔️       | -               |
| image-name  | Image name (format: owner/image)             | ✔️       | -               |
| registry    | Docker registry                              | ❌       | "ghcr.io"       |
| username    | Docker username                              | ❌       | "ddd-cute-bot"  |
| password    | Docker password                              | ✔️       | -               |


Make sure to provide values for all required inputs (tag, image-name, and password) when using the composite action. Optional inputs can be omitted if the defaults are acceptable.
