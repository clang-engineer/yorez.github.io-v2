---
layout  : wiki
title   : ssh로 파일 전송하기
summary : 
date    : 2021-11-05 10:36:15 +0900
updated : 2021-11-21 22:03:06 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

## 일반적인 파일전송
```sh
scp (전송할 파일) (아이디@전송할 서버주소):(저장될 서버의 디렉토리)
```

## ssh 포트 번호가 22번(기본)이 아닌 경우
```sh
scp -P 포트번호 (전송할 파일) (전송할 서버주소@아이디):(저장될 서버의 디렉토리)
```

## 디렉터리를 전송
```sh
scp -P 포트번호 -r (전송할 디렉토리) (전송할 서버주소@아이디):(저장될 서버의 디렉토리)
```

## 공개키를 이용한 파일 전송
scp -i (공개키) -P 22 -r /home/test root@목적지IP:/home
