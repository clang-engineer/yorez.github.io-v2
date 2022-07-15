---
layout  : wiki
title   : Let's Encrypt로 발급 받은 .pem 파일 .key 와 .crt 파일로 변환하기
summary : 
date    : 2022-07-11 11:01:29 +0900
updated : 2022-07-11 11:04:42 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}


1. Let's Encrypt의 인증서 파일 복사
```sh
cp /etc/letsencrypt/live/*  /Desktop/
```

2. .key 파일로 변환하기
```sh
openssl rsa -in privkey.pem -text > [도메인 주소].key
```

3. .crt 파일로 변환하기
```sh
openssl x509 -inform PEM -in fullchain.pem -out [도메인 주소].crt
```


>> 출처: https://hreeman.tistory.com/m/171
