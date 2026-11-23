# docker-base-images
JetLinks docker相关基础镜像

## JDK 21 基础镜像

`jdk/Dockerfile-21` 使用 `eclipse-temurin:21-jdk-noble`，跟随 JDK 21 更新并固定 Ubuntu 24.04 系列。
CI 仅构建并发布 amd64（x64）和 arm64 两种架构，不构建 riscv64。
`pull_request` 仅验证构建，不登录或推送镜像仓库；仅 `master` 分支的 `push` 事件发布镜像到 Docker Hub 和阿里云 ACR。
为兼容阿里云 ACR，两个镜像均关闭 provenance 和 SBOM 证明清单输出；仍保留 amd64/arm64 多架构镜像清单。
两个镜像分别使用 GitHub Actions 构建缓存，避免相同基础镜像和安装命令下重复下载、安装依赖；每次构建仍检查最新基础镜像，上游更新时会重新构建相关层。首次构建或缓存失效时，耗时仍受软件源下载速度影响。
`jdk/Dockerfile-21-all` 基于 `jetlinks/base-jdk-21` 添加流媒体依赖，保持与 noble 的软件包兼容。
