---
layout  : wiki
title   : tableau issue
summary : 
date    : 2021-10-01 10:19:01 +0900
updated : 2022-07-14 11:08:35 +0900
tags    : tableau issue
toc     : true
public  : true
parent  : [[tableau/index]]
latex   : false
---
* TOC
{:toc}

## 문제? 

- Chrome 80 이상으로 업데이트한 후 내장된 뷰를 로드하지 못함

## 현상?  

- embedded 컨텐츠가 로그인 화면으로 보임. 

## 원인? 

- 크롬 80 버전부터 새로운 쿠키 정책이 적용되어 Cookie의 SameSite 속성의 기본값이 "None"에서 "Lax"로 변경됨
- 위의 이유로 태블로 내장뷰와 태블로 서버 통신 과정에서 인증수단으로 사용했던 session 쿠키 전송에 문제가 생겼고, \
인증 토큰의 부재로 iframe콘텐츠들이 로그인 화면으로 리다이렉트되는 현상이 발생하였다.

## SameSite 속성에 대해 변경되는 정책

1. 쿠키를 구울 때 SameSite 옵션이 없는 경우 **Lax** 로 간주한다.
2. SameSite=none 으로 사용하려면 secure옵션(https요청만 허용)을 필수로 한다.
3. http와 https간의 연결은 cross-site로 간주한다.

## SameSite 정책

| 종류   | 접근정책                                                                          |
|--------|-----------------------------------------------------------------------------------|
| None   | 도메인 검증하지 않음. 동일 사이트와 크로스 사이트에 모두 쿠키 전송.               |
|        | ex> A 사이트에서 B 사이트로 요청 전송 시 B 사이트의 쿠키가 붙어서 전송            |
|--------|-----------------------------------------------------------------------------------|
| Lax    | Strict 정책에 예외처리가 몇가지 추가된 정책.                                      |
|        | 예외> get을 사용하는 요청 중 앵커태그. form의 get 메소드.                         |
|--------|-----------------------------------------------------------------------------------|
| Strict | SameSite검사를 강하게 제한하는 정책.  서로 다른 도메인 간 쿠키 전송 불가.         |
|        | 소스가 되는 도메인과 대상 도메인이 일치해야만(자사 도메인o) 쿠키가 포함되어 전송. |
|        | (O) www.google.com => www.google.com , dev.google.com, prod.google.com            |
|        | (X) www.test.com => www.google.com                                                |
    
## 해결방법 ?

1. 자사 도메인을 사용
2. 태블로 서버에서 https를 활성화 시키면 쿠키에 'SameSite=none', 'secure' 옵션이 붙여서 쿠키 전송. \
(* Tableau Server 2019.4.2, 2019.3.4, 2019.2.8, 2019.1.12, 2018.3.14, 2018.2.17 이상 버전으로 업그레이드 필요)

> secure -> 웹브라우저와 웹서버가 https로 통신하는 경우만 웹브라우저가 쿠키를 서버로 전송하는 옵션


> 태블로 공식 대응안:  https://kb.tableau.com/articles/issue/embedded-views-fail-to-load-after-updating-to-chrome-80?lang=ko-kr \
> 구글 SameSite 대응 가이드: https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?hl=ko
> 생활코딩 - 쿠키옵션: https://opentutorials.org/course/3387/21744
