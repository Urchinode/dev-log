---
title: 
date: 2025-04-13 11:15
tags:
  - troubleshooting
  - python
aliases: 
draft: false
---
시스템 파이썬 버전을 유연하게 바꾸기 위해 `pyenv-window`를 사용중이다.
근데, Pycharm에서 인터프리터를 어떻게 설정해야하지?

# pyenv의 경로 찾기

```text title="pyenv 명령어" {} // showLineNumbers{number}
pyenv versions

:: * 3.13.1 (set by C:\Users\******\.pyenv\pyenv-win\version)
```

윈도우 기준 파일 탐색기에서 위의 경로로 들어가면, **버전 폴더**가 있고 들어가서 `python.exe`를 **interpreter로 지정**해두면 된다.

![[pycharm interpreter path example.png]]