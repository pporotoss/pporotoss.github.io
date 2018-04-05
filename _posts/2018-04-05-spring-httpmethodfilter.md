---
layout: post
title: 스프링 HiddenHttpMethodFilter 설정
tags: [Spring, web.xml]
---

# 스프링 HiddenHttpMethodFilter 설정

>html form은 GET과 POST 방식밖에 지원하지 않는다.   
따라서, PUT과 DELETE 방식을 사용하기 위해서는 Javascript를 이용하여 전송하는 방법밖에는 없다.   
하지만, 스프링이 제공하는 HiddenHttpMethodFilter를 설정하게 되면, 약간의 트릭을 이용하여
PUT과 DELETE 를 사용가능하다.


### HiddenHttpMethodFilter 설정
- web.xml에 설정   

```
<filter>
    <filter-name>httpMethodFilter</filter-name>
    <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
</filter>

<filter-mapping>
    <filter-name>httpMethodFilter</filter-name>
    <servlet
</filter-mapping>
```

- JavaConfig 설정   

```
public class MyWebAppInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {

    @Override
        protected Filter[] getServletFilters() {
            return new Filter[] { new HiddenHttpMethodFilter()};
        }

}
```

- html form 태그 사용
   1. form의 method="post"로 설정한다.
   2. hidden form 에다가 name="_hidden"으로 설정후 value에 원하는 방식(PUT, DELETE)를 적어준다.   
   
```
<form name="example" method="post">
    <input type="hidden" name="_hidden" value="PUT" />
</form>

```

- 스프링 태그 사용   

```
<form:form method="delete">
    <p class="submit"><input type="submit" value="Delete Pet"/></p>
</form:form>
```