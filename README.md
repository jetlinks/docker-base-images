# docker-base-images
JetLinks docker相关基础镜像

## JDK 21 基础镜像

`jdk/Dockerfile-21` 使用 `eclipse-temurin:21-jdk-noble`，跟随 JDK 21 更新并固定 Ubuntu 24.04 系列。
CI 仅构建并发布 amd64（x64）和 arm64 两种架构，不构建 riscv64。
`jdk/Dockerfile-21-all` 基于 `jetlinks/base-jdk-21` 添加流媒体依赖，保持与 noble 的软件包兼容。
