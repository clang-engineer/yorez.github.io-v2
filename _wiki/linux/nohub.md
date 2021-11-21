---
layout  : wiki
title   : nohub - 프로세스의 연속
summary : 
date    : 2021-10-14 13:54:41 +0900
updated : 2021-11-21 22:01:41 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# nohub
- **nohub** 명령은 프로세스를 실행한 터미널 세션이 끊기더라도 프로세스가 유지되도록 하는 명령어. \
기본적으로 터미널에서 세션 로그아웃이 발생하면 리눅스는 해당 터미널에서 실행한 프로세스들에게 **HUP signal**을 전달하여 종료시킴. 이 HUP signal을 프로세스가 무시하도록 하는 명령어라서 **nohup**

## nohub [프로세스] &
- 기본 사용법

## nohup [프로세스] 1>/dev/null 2>&1 &
- nohub.out을 생성하지 않기 위해서 표준출력과 표준에러를 /dev/null 로 출력 재지정

