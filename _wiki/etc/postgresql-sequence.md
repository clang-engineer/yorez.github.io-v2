---
layout  : wiki
title   : postgresql 시퀀스 사용법
summary : 
date    : 2021-11-23 11:17:05 +0900
updated : 2021-11-23 11:25:33 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

## 시퀀스 생성

PostgreSQL에서 시퀀스(Sequence)를 사용하는 방법에 대해 알아보자.


## create : CREATE SEQUENCE seq_name
시퀀스 생성

## nextval : nextval('seq_name')
시퀀스 다음값

## currval : currval('seq_name')
시퀀스 현재값

## setval : setval('seq_name', seq_val, [true/false])
시퀀스 초기화
- true : 초기화 후 nextval를 사용할때 초기화된 값(1)에서 +1을 하여 사용된다.
- false : 초기화 후 nextval를 사용할때 초기화된 값(1)을 그대로 사용한다.
 
## drop : DROP SEQUENCE seq_name
