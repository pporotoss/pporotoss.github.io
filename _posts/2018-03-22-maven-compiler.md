---
layout: post
title: 메이븐 컴파일러 플러그인
tags: [Maven]
---

>메이븐 프로젝트로 자바 프로젝트를 생성하면, 기본값으로 자바 1.5로 컴파일이 되기 때문에   
다른버전의 자바로 컴파일 하기 위해서는 maven compiler plugin 을 이용하여 빌드 버전을 명시해야 한다.
      
```      
   <build>
       [...]
       <plugins>
         <plugin>
           <groupId>org.apache.maven.plugins</groupId>
           <artifactId>maven-compiler-plugin</artifactId>
           <version>3.7.0</version>
           <configuration>
             <source>${java-version}</source>
             <target>${java-version}</target>
           </configuration>
         </plugin>
       </plugins>
       [...]
     </build>
```