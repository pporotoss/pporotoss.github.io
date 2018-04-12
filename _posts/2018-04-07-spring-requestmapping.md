---
layout: post
title: Spring - @RequestMapping
tags: [spring]
---

# Spring - @RequestMapping

@RequestMapping 어노테이션은 웹 요청과 컨트롤러의 메서드를 연결지어주는 역할을 한다.  
클래스와 메서드에 적용할 수 있다. 

###※ 적용 가능 속성
   + value : path 속성의 별칭으로 요청 주소를 적어준다.   
   @RequestMapping("/main") 과 @RequestMapping(path="/main") 은 동일하다.
   
   + path : 4.2 버전부터 지원되는 속성으로, value 속성과 동일한 기능을 한다.   
   Ant 스타일의 요청 주소를 지원한다.(ex> /myPath/*.do)
   
   + method : Http 요청 방식을 적어준다. ex> GET, POST, HEAD, OPTIONS, PUT, PATCH, DELETE, TRACE 
   
   + params : 적어준 파라미터명을 클라이언트가 전송하였을때만 연결해준다.   
   "myParam=myValue" 형태로 적어주게 되면 이름이 myValue인 파라미터가 있을때에만 연결하게 되며, "myParam!=myValue" 형태로 적을 경우에는 이름이 myValue인 파라미터가 없을 때만 연결해 준다.  
   
   + headers : 적어준 헤더로 클라이언트가 요청헤더를 전송했을때만 연결해준다.  
    예를들어, "content-type=text/*" 형태로 적어주게 되면 content-type 이 text/로 들어오는 요청만을 연결지어주게 된다.  
    "content-type!=text/*" 형태로도 사용 가능 하다.
        
   + consumes : 적어준 값과 요청헤더의 Content-Type 값이 일치할때만 연결해준다.   
   ex) consumes = {"text/plain", "application/*"} 
    
   + produces : 적어준 값과 요청헤더의 Accept 값이 일치할때만 연결해준다.   
   만약, UTF-8로 인코딩된 JSON값을 응답해야 할 경우에는 "application/json; charset=UTF-8" 라고 적어줘야 한다.   
   ex) produces = {"text/plain", "application/*"}