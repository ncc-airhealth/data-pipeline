# Contributing Guide

## Common

공통 개발 규칙

- 커밋 메시지는 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) 형식을 따르고 영어로 작성

## Docker

[docker/](docker/) 경로 개발 규칙

- 빌드 시 엄격한 재현성을 위해 `amd64` 플랫폼만 허용
- 컨테이너 버전은 다른 컴포넌트와 독립적으로 관리하며 [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html) 규칙을 따름
- Git 태그는 `docker/v1.0.0`, GHCR 이미지 태그는 `1.0.0` 형식 사용
- 게시한 버전은 덮어쓰지 않고 변경 시 새 버전 게시

## Pipeline

[pipeline/](pipeline/) 경로 개발 규칙
