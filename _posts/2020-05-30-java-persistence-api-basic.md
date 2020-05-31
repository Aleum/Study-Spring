---
layout: post
title: Java Persistence API 기본
published: true
date: '2020-05-30'
---
## JPA entity life cycle
- new: no persistent identity, and no association with a persistence context
- managed: persistent identity, and association with a persistence context
- detached: persistent identity, and no association with a persistence context
- removed: persistent identity, association with a persistence context, and scheduled for removal from DB


> persistent identity란, entity가 DB에서 식별가능한 것. (예를 들어 PK값이 entity에 존재하고 그 값이 실제 DB에 있는 특정 row의 값과 일치함.

> persistence context란, managed entity instance의 집합. context 내에서 entity instance가 lifecycle에 위해 관리됨.


### cascade 옵션
- persist operation을 연관된 entity(ManyToOne, OneTo Many 등과 같이)까지 적용할지 결정하는 설정값.


### transient 어노테이션
- persistent 하지 않은 속성이나 필드를 지정함.

## 참고자료
- JSR 220: Enterprise JavaBeans TM,Version 3.0. Java Persistence API
    - https://download.oracle.com/otndocs/jcp/ejb-3_0-fr-oth-JSpec/
- Java Persistence with Hibernate, 2nd Edition