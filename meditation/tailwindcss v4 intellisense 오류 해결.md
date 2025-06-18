---
title:
date: 2025-06-18 22:25
tags: 
aliases: 
draft: false
---
VSCode에는 Tailwind용 Extension으로 `Tailwind CSS IntelliSense` 가 있다.
**AutoComplete 기능**을 제공하는 플러그인이다.
그런데 Tailwind가 v4로 업그레이드 되면서 기능이 제대로 동작되지 않았다.

![[tailwind autocomplete not working example.png]]

# settings.json 설정

1. `설정(Ctrl + ,)` 에 들어가 검색창에 tailwind를 입력한다.
2. `Tailwind CSS › Experimental: Config File`의 `Edit in settings.json` 클릭
3. .css 파일 경로를 입력한다.
```json title="" {} // showLineNumbers{number}
"tailwindCSS.experimental.configFile": "src/styles.css"
```

그러면 AutoComplete가 잘 적용될 것이다.

![[tailwind autocomplete working.png]]