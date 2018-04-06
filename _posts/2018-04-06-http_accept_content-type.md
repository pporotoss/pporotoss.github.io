---
layout: post
title: HttpRequestHeader - Accept
tags: [http]
---

# HttpRequestHeader - Accept

+ Accept : Accept 헤더는 MIME 타입 표현식을 통하여 클라이언트가 해석 가능한 타입들을 요청한다.   
Content Negotiation을 이용하여 서버는 클라이언트가 요청한 사항중에서 하나를 선택하여 클라이언트에게 응답 헤더의 Content-Type을 통해 응답한다.   
클라이언트는 응답받은 Content-Type을 이용하여 서버에서 응답해준 내용들을 해석하게 된다.   

```
Accept: text/html

Accept: image/*

Accept: text/html, application/xhtml+xml, application/xml;q=0.9, */*;q=0.8
```
