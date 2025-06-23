---
title: 
date: 2025-06-23 20:52
tags:
  - concept
  - ci-cd
  - github-actions
aliases: 
draft: false
---
### CI/CD
>[!info]
>push, pull request 등으로 변경될 때마다 **자동으로 빌드, 테스트, 배포**하는 자동화 파이프라인을 구성하는 데 사용

**예시:**
- **Push할 때마다** 단위 테스트를 자동 실행
- 코드 머지 시 **AWS, GCP, Azure, Vercel, Netlify** 등으로 **자동 배포**
- Docker 이미지를 자동 빌드 후 Docker Hub로 푸시

### 코드 정적 검사
>[!info]
>**코드 스타일 검사(lint), 보안 취약점 검사, 정적 코드 분석** 등을 자동으로 수행

### 이슈/PR 관리 자동화
>[!info]
>이슈와 Pull Request에 **라벨 자동 추가, 이슈 자동 할당, 메시지 자동 응답** 등을 처리

---
# 기본 개념
- `workflows`: 자동화 작업 집합
	- `.github/workflows` 폴더에 **yml 파일** 작성
- `event`: 워크플로우 트리거 조건
- `job`: 작업 실행 단위
- `step`: `job`의 세부 실행 단위
- `runner`: 실행 환경(`ubuntu-latest`)
- `Secret`: 민감한 정보 관리
- `artifacts`: 저장된 결과물

# Gradle CI 예시
```yaml title="" {} // showLineNumbers{number}
name: Gradle Build CI

on:           # [Event] - 워크플로우를 트리거하는 조건
  push:
    branches: [ "main" ]   # main 브랜치에 푸시될 때 실행

jobs:
  build:      # [Job] - 독립적 실행 단위, 이름은 build
    runs-on: ubuntu-latest   # [Runner] - 깃허브에서 제공하는 VM 환경 지정

    steps:    # [Step] - 세부 실행 단계의 모음
      - name: Checkout repository code
        uses: actions/checkout@v4    # 소스코드 체크아웃(액션 활용 예시)

      - name: Set up JDK 17
        uses: actions/setup-java@v4  # 공식 액션 활용해 JDK 설치
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Grant execute permission for gradlew
        run: chmod +x ./gradlew      # gradlew 실행권한 부여

      - name: Build with Gradle
        run: ./gradlew build         # gradle 빌드 실행

      - name: Use secret token
        run: echo "Using secret ${{ secrets.MY_SECRET_TOKEN }}"   # [Secret] - 보안 정보 활용 예시
        env:
          MY_SECRET_TOKEN: ${{ secrets.MY_SECRET_TOKEN }}

      - name: Upload build artifacts
        uses: actions/upload-artifact@v4     # 빌드 산출물 저장(공식 액션)
        with:
          name: build-result
          path: build/libs/*.jar
```

## 궁금한 점들
1. 상황에 따라 `runs-on`에 무엇을 적어야하는지 어떻게 아나?
	1. 배포 환경에 맞게 설정하는 것이 좋다.(대부분 `ubuntu-latest`)
	2. 특정 OS에서 빌드하는 프로젝트는 `windows-latest`, `macos-latest` 등을 사용한다.
2. `step`의 `uses`란?
	1. Github Marketplace에 있는 **재사용 가능한 액션**이다.
	- `actions/checkout@v4` → 깃허브 공식 코드 체크아웃 액션
	- `actions/setup-java@v4` → 깃허브 공식 JDK 설치 액션
    - `actions/upload-artifact@v4` → 빌드 결과물 업로드 액션
3. `with`의 용도
	1. `uses`로 불러온 **액션에 전달하는 설정값/옵션**
	2. 해당 액션에 어떤 설정값들이 있는지 확인해주자
	3. 이런 설정값을 정의하려면 `input`을 사용한다.
```yaml title="" {} // showLineNumbers{number}
inputs:
  my-option:
    description: '설정값 설명'
    required: true
    default: '기본값'
```
4. `artifact` 확인하는 방법
	1. `Actions` 메뉴에서 확인한다.