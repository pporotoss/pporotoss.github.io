---
layout: post
title: Spring - remember-me 설정
tags: [spring, security]
---

# Spring - remember-me 설정


+ 토큰 정보를 저장하기 위한 테이블을 생성한다.   

```
create table persistent_logins (username varchar(64) not null,
								series varchar(64) primary key,
								token varchar(64) not null,
								last_used timestamp not null)

```   

+ 토큰 정보를 저장하기 위한 PersistentTokenRepository 인터페이스를 구현한 클래스를 Bean으로 등록한다.
   + 기본 제공되는 JDBC 기반의 JdbcTokenRepositoryImpl 를 사용하거나, PersistentTokenRepository 인터페이스를 직접 구현한다.
   + JdbcTokenRepositoryImpl 클래스 사용시에는 DataSource를 반드시 setter 메서드로 설정해줘야 한다.

+ 스프링 시큐리티가 사용자 정보를 조회하기 위해 UserDetailsService를 Bean으로 등록한다.

+ WebSecurityConfigurerAdapter를 상속받은 환경설정 클래스를 만든다.

+ protected void configure(HttpSecurity http) 메서드를 아래와 같이 재정의 한다.

```
protected void configure(HttpSecurity http) throws Exception {
		
    http
        .rememberMe() // remember-me 활성화
        .rememberMeParameter("remember-me") // form 에서 전송할 파라미터명
        .userDetailsService(userDetailsService) // 시큐리티가 user 정보를 조회할 때 사용하는 UserDetailsService 설정
        .tokenRepository(jpaTokenRepository) // remember-me 관련 정보를 조회하기 위한 PersistentTokenRepository 설정
        .tokenValiditySeconds(60*60) // remember-me 쿠키 지속시간
}
```  

> configure(HttpSecurity http) 메서드에서 절대 .anyRequest().fullyAuthenticated() 를 설정해서는 안된다.   
fullyAuthenticated() 는 remember-me를 허용하지 않기 때문이다.   
따라서, remember-me 기능을 사용하려면 반드시 .anyRequest().authenticated() 를 이용해야 한다.

