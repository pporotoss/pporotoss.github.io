---
layout: post
title: Ubuntu Nginx 포워딩 설정
tags: [Nginx]
---

# Ubuntu Nginx 포워딩 설정

1. 편집기를 이용하여 /etc/nginx/sites-enabled/default 파일을 연다.
1. 기본설정된 server directive 부분에서 location / { 부분을 찾아서 아래의 설정을 추가한다.

```
proxy_pass http://localhost:8080;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $http_host; 
```   
