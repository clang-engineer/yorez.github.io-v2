---
layout  : wiki
title   : 사설 인증서 생성하기
summary : 
date    : 2021-11-08 14:24:46 +0900
updated : 2021-11-21 22:05:01 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

## 1단계 - 개인키 생성하기

```sh
openssl genrsa -des3 -out private.key 2048
```

## 2단계 - csr 성성하기
인증서 발급에 필요한 내용을 담고 있는 요청서. 1단계에서 생성한 key를 가지고 요청서를 생성합니다.

```sh
openssl req -new -key private.key -out public.csr
```

## 3단계 - 개인키에서 패스워드 제거 
패스위드를 제거한 인증서 (apache, nginx 등 데몬 재구동할 때마다 패스워드를 입력해야하는 볼편함 없애기 위해)
```sh
openssl rsa -in private.key -out private_nopass.key
```

## 4단계 - 사설 인증서 생성
```sh
openssl x509 -req -days 3650 -in public.csr -signkey private.key -out public.crt
```

## 인증서 정보 확인
```sh
openssl x509 -in public.crt -text -noout
```

## 개인키 패스워드 확인
```sh
openssl rsa -check -in private.key
```
