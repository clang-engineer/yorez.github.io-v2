---
layout  : wiki
title   : ajax Set타입 데이터 전송 안될 때
summary : 
date    : 2021-12-02 10:26:24 +0900
updated : 2021-12-02 12:57:36 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

ajax 요청 몸통에 typescript에서 제공하는 set type의 데이터를 전송하려할 때 자꾸 null로 날라가는 현상이 있었다.
배열 주소 참조의 이슈로 추정되는데 [...new Set()]과 같이 새로 복사해서 할당한 리스트는 정상적으로 발송 되었다.
