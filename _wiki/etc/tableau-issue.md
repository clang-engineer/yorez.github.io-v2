---
layout  : wiki
title   : tableau issue
summary : 
date    : 2021-10-01 10:19:01 +0900
updated : 2021-10-05 12:58:16 +0900
tags    : tableau issue
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# Tableau Issue

## Chrome 80 이상으로 업데이트한 후 내장된 뷰를 로드하지 못함

현상?  

embedded 컨텐츠가 로그인 화면으로 보임. 

원인? 

크롬에서 보안이슈(csrf)를 이유로 80버전부터는 third party(웹서비스와 도메인이 다른 서버)에서 쿠키심는 걸 기본적으로 차단하는 정책을 적용했다 한다. \
때문에, 태블로 내장뷰와 태블로 서버 통신 과정에서 인증수단으로 사용했던 session 쿠키 생성에 문제가 생겼고, \
인증 토큰의 부재로 iframe콘텐츠들이 로그인 화면으로 리다이렉트되는 현상이 발생하였다.

해결 ?

쿠키에 'SameSite=none', 'secure'를 설정하면 third party에서 예외적으로 쿠키생성이 가능한 예외조항이 있었다. \
때문에, thrid party(태블로서버)에서 쿠키생성시 해당 옵션을 적용한 쿠키를 생성하도록 정책이 변경되었다. \
쿠키에 적용된 secure 속성은 https 를 통해만 정상 발송 되므로 embedded 뷰를 사용하던 기존 사이트들은 통신하는 태블로서버에 https을 적용함으로써 크롬 이슈를 해결할 수 있었다. 

> https://kb.tableau.com/articles/issue/embedded-views-fail-to-load-after-updating-to-chrome-80?lang=ko-kr \
> https://brocess.tistory.com/263
