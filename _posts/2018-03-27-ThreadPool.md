---
layout: post
title: 쓰레드풀
tags: [Thread]
---

# 자바 쓰레드풀

>쓰레드는 새로운 쓰레드를 생성하기위해 많은 컴퓨터 자원을 소모한다.   
그리고 컴퓨터 자원은 한정되어 있기때문에 쓰레드를 무한정 생성할 수도 없다.   
한정된 컴퓨터자원을 좀 더 효율적으로 사용하기위해서는 쓰레드풀에 필요한만큼   
쓰레드를 미리 만들어 놓고 사용하는것이 좋다.

#### 쓰레드풀의 생성
쓰레드풀을 생성하는 방법은 ThreadPoolExecutor 객체를 직접 생성하는 방법과,   
Excutors 클래스의 스태틱 매서드를 이용하여 만드는 방식이 있다.
1. ThreadPoolExecutor 객체를 이용하여 생성 
   + ThreadPoolExecutor 객체를 생성하기 위해서는 다양한 생성자 매개변수를 설정해야 한다.
   + corePoolSize : 최소한으로 유지될 스레드의 수.    
   쓰레드를 이용한 작업이 실행되면 쉬고 있는 쓰레드가 존재하더라도, corePoolSize까지 쓰레드를 생성한다. 
   + maximumPoolSize : 최대로 생성할 스레드의 갯수를 지정.
   + keepAliveTime : corePoolSize를 초과하는 스레드가 유지되는 시간.
   + TimeUnit : keepAliveTime의 시간 단위를 설정.
   + BlockingQueue : 쓰레드가 corePoolSize 만큼 생성되어있고 쉬고 있는 쓰레드가 없으면,   
   쓰레드를 생성하기전에 BlockingQueue에 작업이 대기하게 된다.   
   BlockingQueue가 꽉차게 되면, 새로운 쓰레드를 maximumPoolSize까지 생성한다.
   + ThreadFactory : 쓰레드를 생성하는데 사용되는 객체. 매개변수로 입력하지 않으면 기본 ThreadFactory를 사용한다.
   + RejectedExecutionHandler : 큐에 작업이 가득차 있고 쓰레드가 최대치까지 생성되어 작업 수행이 불가능하거나, Excutor가 종료되었을때 수행해야 할 내용들을 정의한다.  
   기본값은 ThreadPoolExecutor.AbortPolicy 이다.
2. Executors의 스태틱 매서드를 이용하여 생성
   + Executors.newCachedThreadPool() : 쓰레드를 계속하여 생성한다. 이전에 생성한 쓰레드가 재사용 가능하면 재사용한다.
   + Executors.newFixedThreadPool(int nThreads) : 지정한 갯수만큼만 쓰레드를 생성한다.
   + Excutors.newScheduledThreadPool(int corePoolSize) : ScheduledExecutorService 를 통하여 스케쥴링 가능한 쓰레드를 생성한다.
   + Excutors.newSingleThreadExecutor() : 오직 하나의 쓰레드만 생성한다.
   + Excutors.newSingleThreadScheduledExecutor() : 스케쥴링가능한 쓰레드를 오직 하나만 생성한다.
   + Excutors.newWorkStealingPool() : 동시수행이 가능할 정도의 쓰레드양을 유지시켜주는 쓰레드를 생성한다.