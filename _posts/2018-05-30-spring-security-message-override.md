---
layout: post
title: 스프링 시큐리티 메시지 재정의하기
tags: [spring, spring-security]
---

# 스프링 시큐리티 메시지 재정의하기

- 스프링 시큐리티로 로그인 치리시, 로그인이 실패하면 BadCredentialsException이 발생하게 된다.
- BadCredentialsException은 AbstractUserDetailsAuthenticationProvider에서 로그인 처리중 생성한다.  
- BadCredentialsException에 담긴 메시지는 spring-security-core.jar 파일안에 담긴 messages.properties 파일을 이용한다.
- AbstractUserDetailsAuthenticationProvider는 메시지를 SpringSecurityMessageSource 를 이용하여 가져온다.
- SpringSecurityMessageSource는 메시지 파일의 basename을 'org.springframework.security.messages' 로 설정해 놓았다. 
- 따라서 스프링 시큐리티에서 발생하는 Exception의 메시지를 재정의하기 위해서는 아래와 같은 작업이 필요하다.
   1. 프로젝트 파일에 org.springframework.security 패키지를 생성한다.
   2. 생성한 패키지 안에 spring-security-core.jar 파일 안에 포함된 messages.properties 파일들을 복사해온다.
   3. 복사해온 messages.properties 파일을 열어 필요한 값만 수정해준다.
   4. messages.properties 파일은 Locale 이 써진 파일이 우선 적용되게 된다.

- BadCredentialsException의 메시지는 세션에 담긴 SPRING_SECURITY_LAST_EXCEPTION 을 통해서도 조회 가능하다.