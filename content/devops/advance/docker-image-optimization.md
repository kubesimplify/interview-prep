---
title: "Docker Image Optimization"
date: 2026-01-13
author: "KubeSimplify"
draft: false
weight: 20
description: "Reducing size and improving build speed of Docker images."
---

### Scenario

A microservice's Docker image has grown to 1.5GB, slowing down deployments and consuming excessive storage. The Dockerfile installs dependencies, builds the Go application, and runs it.

### Question

Describe how you would refactor this Dockerfile to significantly reduce the image size and improve build times.

### Expected Answer

1.  **Multi-Stage Builds**: Use a build stage (with full SDK) to compile the binary, and a runtime stage (distroless or alpine) for the final image.
2.  **Layer Caching**: Order instructions from least changed to most changed (COPY `go.mod` -> `go mod download` -> COPY source -> `go build`).
3.  **Minimal Base Image**: Use `gcr.io/distroless/static` or `alpine` for the final stage.
4.  **Impact**: Expect size reduction to <50MB and faster sequential builds due to better caching.
