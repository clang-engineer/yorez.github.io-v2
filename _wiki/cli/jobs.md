---
layout  : wiki
title   : job관리 - linux 프로세스 일시 중단 
summary : 
date    : 2021-10-14 13:38:06 +0900
updated : 2021-10-14 14:13:16 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# job
- job은 shell에서 실행한 process를 의미한다. shell은 내부적으로 job table로 해당 process 정보를 유지한다.

## jobs
- background 작업들과 각 상태들을 보여줌
 
## ctrl + z
- foreground 작업을 중지하고 background로 옮김

## bg %n
- background 에서 작업을 실행

## fg %n
- background 작업을 foreground 로 옮김

## kill %n
- 작업을 끝냄 
- %이 빠지면(ex> kill n) PID가 n인 프로세스를 강제 종료하므로 주의

## background 작업을 중지시키기
- fg %n을 통해서 foreground로 가져온 후 ctrl + z로 중지

