---
layout  : wiki
title   : nikto를 통한 취약점 점검
summary : 
date    : 2021-10-18 09:09:57 +0900
updated : 2021-10-18 09:45:13 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]] 
latex   : false
---
* TOC
{:toc}

# Nikto
**<https://github.com/sullo/nikto>** \\
웹서버 취약점을 분석해주는 오픈소스 툴

디렉터리 인덱싱, XSS, 

## 특징
- Perl 기반
- gpl 라이센스 

## 설치
brew install nikto

## 사용법
nikto -h [host ip] -port [port number] -C all

## 옵션

| 옵션          | 설명                                                    |
|---------------|---------------------------------------------------------|
| -h<br>-host   | 타겟주소                                                |
| -o<br>-output | 출력결과 파일 지정<br>format 옵션을 사용해 포맷을 지정  |
| -C            | 목표 웹 서버의 CGI 디렉터리를 지정하는데,  all 사용권장 |
| -config       | 설정파일 지정                                           |
| -port         | 포트지점                                                |
| -cookie       | 쿠키표시                                                |
| -ssl          | ssl을 사용하는 티켓에 사용                              |
