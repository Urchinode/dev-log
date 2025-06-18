---
title: 
date: 2025-06-06 18:31
tags:
  - concept
  - golang
aliases: 
draft: false
---
# go.mod
>[!info] Go 버전, 모듈 정보, 패키지를 관리하는 파일

**go.mod** is the module definition file that:

- Declares the module name and Go version requirement
- Lists direct dependencies with their versions
- Contains replace directives and exclusions if needed
- Is human-readable and editable
# go.sum
> [!info] 의존성 해시값을 저장해서 정확한 버전을 보장하는 파일

**go.sum** is the checksum database that:

- Contains cryptographic checksums for all dependencies (direct and indirect)
- Ensures dependency integrity and prevents tampering
- Is automatically generated and maintained by Go tools
- Should not be manually edited

# 패키지 명령어
| 명령어                 | 용도 및 설명                                            |
| ------------------- | -------------------------------------------------- |
| `go get 패키지`        | 의존성 추가(새 패키지 설치, go.mod에 반영, Go 1.17 이후 추가/업그레이드용) |
| `go get -u 패키지`     | 명시 패키지 및 하위 의존성 최신 버전으로 업그레이드                      |
| `go install 패키지@버전` | 특정 버전의 바이너리 패키지 직접 설치 (go.mod 반영 안함, 툴 설치용)        |
| `go mod tidy`       | go.mod와 go.sum 정리, 필요 없는 의존성 제거, 필요한 의존성 자동 추가     |
| `go mod vendor`     | vendor 폴더 생성(의존성 코드를 로컬로 복사, 오프라인 빌드에 사용)          |
| `go list -m all`    | 현재 모듈이 사용하는 모든 의존성 리스트 확인                          |
