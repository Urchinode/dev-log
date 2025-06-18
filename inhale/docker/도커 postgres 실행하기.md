---
title: 
date: 2025-06-04 20:45
tags:
  - concept
  - docker
aliases: 
draft: false
---
# 이미지 pull
```bash title="" {} // showLineNumbers{number}
docker pull postgres
```

# 도커 컨테이너 실행
```bash title="" {} // showLineNumbers{number}
docker run --name mydb -e POSTGRES_PASSWORD=123456 -p 5432:5432 -v /custom/local/path:/var/lib/postgresql -d postgres
```