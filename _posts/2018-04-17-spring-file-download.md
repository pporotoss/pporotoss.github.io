---
layout: post
title: Spring - 파일다운로드 헤더 설정
tags: [spring, filedownload]
---

# Spring - 파일다운로드 헤더 설정

+ Content-Disposition: inline; filename=파일이름
   + inline : 브라우저 안에 파일내용 표시
   + attachment : 파일 다운로드창 표시
+ Content-Transfer-Encoding: binary
+ Content-Type: 파일 MIME-TYPE
+ Content-Length: 파일크기
+ Cache-Control: no-cache, no-store, must-revalidate

> 파일 한글명이 깨질때는 파일명을 UTF-8 -> ISO-859-1 로 인코딩해야 한다.   
ex) new String(fileName.getBytes("UTF-8"), "ISO-859-1"); 


