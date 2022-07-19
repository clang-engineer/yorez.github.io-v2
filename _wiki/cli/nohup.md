---
layout  : wiki
title   : nohup
summary : 세션종료에 따른 프로세스 종료를 막아주는 nohup
date    : 2021-10-14 13:54:41 +0900
updated : 2022-07-19 14:00:51 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# nohup
- **nohup** 명령은 프로세스를 실행한 터미널 세션이 끊기더라도 프로세스가 유지되도록 하는 명령어. \
기본적으로 터미널에서 세션 로그아웃이 발생하면 리눅스는 해당 터미널에서 실행한 프로세스들에게 **HUP signal**을 전달하여 종료시킴. 이 HUP signal을 프로세스가 무시하도록 하는 명령어라서 **nohup**

## nohup과 &(백그라운드) 차이
- nohup 은 세션이 종료되더라도 프로그램이 종료되지 않지만, &은 로그아웃으로 세션 연결이 끊어지면 실행되고 있던 프로그램도 함께 종료됨

## nohup [프로세스] & 
- nohup + &은 어떤 프로그램을 종료 없이 백그라운드에서 실행시키고 싶을 때 사용
  
## nohup 사용 예시
> 0: 표준 입력, 1: 표준 출력, 2: 표준 에러

### 표준출력과 표준에러를 다른 파일에 쓰고 싶을 때
```sh
nohup ./sample.sh 1 > sample.out 2 > sample.err &
```

### 표준출력과 표준에러를 같은 파일에 쓰고 싶을 때
```sh
nohup ./sample.sh 1 > sample.out 2 > &1 &
```

### nohup.out을 생성하고 싶지 않을 때
- nohup [프로세스] 1>/dev/null 2>&1 &
- nohup.out을 생성하지 않기 위해서 표준출력과 표준에러를 /dev/null 로 출력 재지정
 
```sh
nohup ./sample.sh 1>/dev/null 2>&1 &
```

