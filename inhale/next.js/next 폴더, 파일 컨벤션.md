---
title: 
date: 2025-06-14 14:00
tags:
  - concept
  - nextjs
aliases: 
draft: false
---
[`Project structure and organization`](https://nextjs.org/docs/app/getting-started/project-structure#top-level-folders)

# 폴더
## 기본 구조

|                                                                                      |                                    |
| ------------------------------------------------------------------------------------ | ---------------------------------- |
| [`app`](https://nextjs.org/docs/app/building-your-application/routing)               | App Router                         |
| [`pages`](https://nextjs.org/docs/pages/building-your-application/routing)           | Pages Router                       |
| [`public`](https://nextjs.org/docs/app/api-reference/file-conventions/public-folder) | Static assets to be served         |
| [`src`](https://nextjs.org/docs/app/api-reference/file-conventions/src-folder)       | Optional application source folder |

## 동적 라우트
| | |
|---|---|
|[`[folder]`](https://nextjs.org/docs/app/api-reference/file-conventions/dynamic-routes#convention)|Dynamic route segment|
|[`[...folder]`](https://nextjs.org/docs/app/api-reference/file-conventions/dynamic-routes#catch-all-segments)|Catch-all route segment|
|[`[[...folder]]`](https://nextjs.org/docs/app/api-reference/file-conventions/dynamic-routes#optional-catch-all-segments)|Optional catch-all route segment|
# 파일
## 기본 컴포넌트
![[next.js basic file components.png]]
# 폴더 컨벤션
1. `app` 의 하위 **폴더 이름이 곧 URL 경로**.
2. 단, `page.js` 또는  `route.js`가 존재해야 접근할 수 있다.
3. `_`로 시작하는 폴더는 `private`하다. (`page.js/route.js` 존재해도 접근 안됨)

# 파일 컨벤션
1. `page.js`가 기본 페이지 컴포넌트이다.
2. `layout.js`는 **여러 페이지에서 공용으로 사용**할 컴포넌트이다.
	1. `app` 폴더에 **반드시 루트 레이아웃이 정의돼야** 한다.
	2. 레이아웃이 `page.js`**를 감싸는 역할**을 한다.
3. `[slug]` 를 이용해 조건별 페이지 컴포넌트를 정의할 수 있다.