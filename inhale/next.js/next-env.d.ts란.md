---
title: 
date: 2025-06-14 12:56
tags:
  - concept
  - nextjs
aliases: 
draft: false
---
# .d.ts란
>[!info] 타입스크립트 선언 파일
>**JS 라이브러리의 타입 정보**를 TS 컴파일러에게 알려주는 용도

## 예시 JS
```js title="" {} // showLineNumbers{number}
// math.js
export function add(a, b) {
  return a + b;
}

export class Calculator {
  multiply(x, y) {
    return x * y;
  }
}
```
## d.ts 만들기
```ts title="" {} // showLineNumbers{number}
export function add(a: number, b: number): number;

export class Calculator {
  multiply(x: number, y: number): number;
}
```

# next-env.d.ts란
>[!info]
> Next.js 전용 타입을 TS 컴파일러에게 알려주는 용도

```ts title="" {} // showLineNumbers{number}
/// <reference types="next" />
/// <reference types="next/image-types/global" />

// NOTE: This file should not be edited
// see https://nextjs.org/docs/app/api-reference/config/typescript for more information.

```
`///`가 붙은 라인은 XML 태그 형태의 TS 컴파일러 지시어이다.
`types`에 해당되는 `@types/keyword` 또는 `keyword/types` 내의 `d.ts` 파일을 import하는 역할을 한다.