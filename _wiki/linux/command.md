---
layout  : wiki
title   : linux command
summary : 
date    : 2021-10-07 10:31:41 +0900
updated : 2021-10-13 15:16:01 +0900
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

## 명령어 실행
### ;
- 성공여부와 상관없이 다음 명령어 실행
```
mkdir test; cd test
```

### &&
- 성공한 경우에 다음 명령어 실행
```
mkdir test && mkdir test && touch abc
```
1. mkdir test(실패) - 이름 중복
2. touch abc(성공)
```
// test라는 폴더가 같은 폴더에 존재한다는 가정
mkdir test; touch abc
```
1. mkdir test(실패) - 이름 중복
2. touch abc(성공)
