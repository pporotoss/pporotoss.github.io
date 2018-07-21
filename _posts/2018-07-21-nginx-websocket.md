---
layout: post
title: NGINX 웹소켓 설정
tags: [nginx, websocket]
---

# NGINX 웹소켓 설정

NGINX에서 웹소켓을 사용하기 위해서는 아래와 같은 설정을 추가해줘야 한다.  

```
        # WebSocket support (nginx 1.4)
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
``` 