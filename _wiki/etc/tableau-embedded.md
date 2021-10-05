---
layout  : wiki
title   : tableau embedded
summary : 
date    : 2021-10-01 10:19:01 +0900
updated : 2021-10-05 10:55:41 +0900
tags    : tableau
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# Tableau Embedded

회사에서 구축한 사이트에 태블로 화면을 내장할 수 있도록하는 작업을 진행했다.
작업 과정에서 몇가지 이슈가 있었어서 기록으로 남기고자 한다.

## Ticket 발급

우선적으로 태블로서버로부터 인증된 티켓을 발급받는 과정이 필요하다.
[https://help.tableau.com/current/server/ko-kr/trusted_auth_webrequ.htm]

### 신뢰할 수 있는 ip 추가
티켓 발급을 요청하는 host ip 또는 대역이 태블로 서버에 등록되어 있어야한다.
https://help.tableau.com/current/server/ko-kr/trusted_auth_trustIP.htm

### 
