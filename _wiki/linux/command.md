---
layout  : wiki
title   : linux command
summary : 
date    : 2021-10-07 10:31:41 +0900
updated : 2021-10-14 10:48:48 +0900
tag     : linux command
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# 유용한 리눅스 명령어 정리

## job
- job은 shell에서 실행한 process를 의미한다. shell은 내부적으로 job table로 해당 process 정보를 유지한다.

### jobs
- background 작업들과 각 상태들을 보여줌
 
### ctrl + z
- foreground 작업을 중지하고 background로 옮김

### bg %n
- background 에서 작업을 실행

### fg %n
- background 작업을 foreground 로 옮김

### kill %n
- 작업을 끝냄 
- %이 빠지면(ex> kill n) PID가 n인 프로세스를 강제 종료하므로 주의

### background 작업을 중지시키기
- fg %n을 통해서 foreground로 가져온 후 ctrl + z로 중지

---
## 명령어 실행 방법
### ;
- 성공여부와 상관없이 다음 명령어 실행
```
mkdir test; cd test
```

### &&
- 앞의 명령어가 성공한 경우만 다음 명령어 실행
 
```
// 이미 test폴더가 있을 경우
// 아래 1. 2. 예시 'mkdir test'명령은 동일하게 실패하지만, 따라오는 명령어 실행 결과는 다름
1. &&으로 연결할 경우
mkdir test && cd test && touch abc (실패, 실행x, 실행x)

2. ;으로 연결할 경우
mkdir test; cd test; touch abc (실패, 실행o, 실행o)
```

### &
- 명령어를 백그라운드로 동작시킬 때 사용
```
// test 디렉터리 생성과 test이동을 동시에 하려하기 때문에 존재하지 않는 폴더에 이동하려고 하는 것처럼 인식됨(순차 실행 x). 
mkdir test & cd test (성공, 실패)
```

### 명령의 그룹핑
- mkdir test 성공했을 경우 {}안의 명령어 그룹을 실행, 실패했을 경우 || 뒤의 명령어를 실행
```
mkdir test && { cd test; touch abc; echo 'success!!' } || echo 'fail to make dir';
```

---
## nohub
**nohub** 명령은 프로세스를 실행한 터미널 세션이 끊기더라도 프로세스가 유지되도록 하는 명령어. \
기본적으로 터미널에서 세션 로그아웃이 발생하면 리눅스는 해당 터미널에서 실행한 프로세스들에게 **HUP signal**을 전달하여 종료시킴. 이 HUP signal을 프로세스가 무시하도록 하는 명령어라서 **nohup**

### nohub [프로세스] &
- 기본 사용법

### nohup [프로세스] 1>/dev/null 2>&1 &
- nohub.out을 생성하지 않기 위해서 표준출력과 표준에러를 /dev/null 로 출력 재지정


---
## lsof
시스템에 있는 모든 열린 파일들에 대한 정보를 출력

---
## ps

---
## netstat
