---
layout  : wiki
title   : 도커 폐쇄망 설치
summary : 
date    : 2022-04-06 14:22:27 +0900
updated : 2022-04-06 14:25:51 +0900
tags    : 
toc     : true
public  : true
parent  : [[docker/index]]
latex   : false
---
* TOC
{:toc}

# 도커 폐쇄망 설치 히스토리

> https://docs.docker.com/engine/install/binaries/

## 1. 바이너리 적당한 거 다운로드

## 2. 압축해제
 
```sh 
$ tar xzvf /path/to/<FILE>.tar.gz
```

## 3. 전역 실행경로로 복사 
 
```sh
$ sudo cp docker/* /usr/bin
```

## 4. 도커 데몬 실행 
 
```sh
$ sudo dockerd & 
```

## 5. 도커 실행 확인 
 
```
$ sh sudo docker run hello-world
```

