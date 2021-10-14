---
layout  : wiki
title   : 윈도우 서비스 등록 및 관리 방법
summary : 
date    : 2021-10-14 10:52:35 +0900
updated : 2021-10-14 14:30:31 +0900
tags    : 
toc     : true
public  : true
parent  : [[window/index]]
latex   : false
---
* TOC
{:toc}

## sc로 서비스 관리 
cmd에서 sc커맨드를 통한 서비스 관리가 가능하다

### sc create [서비스명] binpath= [서비스 파일 경로]
- binpath 뒤에 공백을 한칸 입력해줘야함

### sc delete [서비스명]
- 서비스 삭제
 
### sc start [서비스명]
- 등록된 서비스 실행
 
### sc stop [서비스명]
- 등록된 서비스 정지
 
### sc query [서비스명]
- 서비스 조회


## nssm로 서비스 관리
- 다운로드: <http://nssm.cc/download>
- java를 실행하는 batch 파일을 서비스로 등록할 때 nssm을 사용하면 손쉽게 등록 할 수 있다.
 
```batch
@ECHO OFF

cd /D "c:\work"
java -jar startup.jar
```
위와 같은 배치 파일 생성후
1. cmd 열기
2. 다운 받은 nssm.exe가 존재하는 폴더로 이동
3. nssm.exe install \<service name\>

![nssm image](https://user-images.githubusercontent.com/39648594/137248149-c554b7b1-32b5-445b-a483-087abcdb850d.png) 

gui 가 나타나고 **application tab -> path에서 실행파일 경로 설정 -> install service** 순으로 진행하면 
서비스가 정상적으로 등록된 걸 확인할 수 있다.
