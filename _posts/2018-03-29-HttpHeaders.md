---
layout: post
title: Http Messages
tags: [HTTP]
---

# Http Messages

### HTTP 메시지는 Request와 Response로 나뉜다.

※Request 양식
>Request-Line _CRLF_   
Request Headers _CRLF_
_CRLF_   
Message-Body

※Response 양식
>Status-Line   
Response Headers _CRLF_   
_CRLF_   
Message-Body

1. Request
   1. Request-Line : Http요청의 첫번째 줄로써 필수로 전송해야 한다.  
   Request-Line의 모든 정보는 case-sensitive 하다. 
   Method, URI, HttpVersion 순으로 위치한다.   
   Method *SP* Request-URI *SP* HTTP-Version *CRLF*  
   ex) GET /index.html HTTP/1.1
   
   2. Header   
   헤더는 :(colon) 문자 + 공백을 기준으로 이름과 값을 구분한다.   
   각각의 헤더라인은 *CRLF*(캐리지리턴) 으로 구분된다.     
   ex) Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
   
   3. Message-Body : 요청시 전달하는 값들이 오게 된다.
   
 2. Response
    1. Status Line : Http 응답의 첫번째 줄로써 필수 값이다.  
    Http버전, Http상태코드, Reason Phrase 순으로 위치한다.   
    Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF
    
    2. Header : Request 헤더와 동일
    
    3. Message-Body : 서버가 전달하는 값들이 오게 된다.
   