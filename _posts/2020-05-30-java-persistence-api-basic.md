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


> persistence context란, DB context와 application context가 연결된 상태. (러프하게)


### cascade 옵션
- persist operation을 연관된 entity(ManyToOne, OneTo Many 등과 같이)까지 적용할지 결정하는 설정값.
