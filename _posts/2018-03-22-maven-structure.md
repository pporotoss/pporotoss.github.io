---
layout: post
title: 메이븐 기본 구조
tags: [Maven]
---

# 메이븐 프로젝트 기본 폴더 구조

- src/main/java : 자바 파일 위치하는곳
- src/main/resources : xml, properties 같은 파일들이 위치하는곳
- src/main/webapp : 웹 어플리케이션 파일들이 위치하는곳
- src/test/java : 테스트용 자바 클래스 위치하는곳
- src/test/resources : 테스트용 xml, properties 같은 파일들이 위치하는곳

>메이븐은 기본적으로 src/main/java 폴더에서는 자바파일만을 빌드하기때문에,   
   src/main/java 폴더에 리소스 파일이 있다면,   
   pom.xml 파일에 메이븐 resources 플러그인 설정을 해야 한다.
      
```      
   <build>
       ...
       <resources>
         <resource>
           <directory>src/main/java</directory>
           <includes>
             <include>**/*.xml</include>
           </includes>
         </resource>
         ...
       </resources>
       ...
     </build>
```