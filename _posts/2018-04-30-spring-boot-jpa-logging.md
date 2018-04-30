---
layout: post
title: SpringBoot - hibernate sql 로그설정
tags: [spring boot, hibernate, logging]
---

# SpringBoot - hibernate sql 로그설정

+ spring.jpa.show-sql=true 설정만으로 sql 로그를 출력 가능하지만, ? 에 바인딩 된 값 또한 출력하기 위해 아래와 같이 설정해준다.

```
logging.level.org.hibernate.SQL=DEBUG  # sql 출력
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE  # ? 에 바인딩 된 값 출력 
```   
