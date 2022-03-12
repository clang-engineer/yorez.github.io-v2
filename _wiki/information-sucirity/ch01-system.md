---
layout  : wiki
title   : ch01 시스템
summary : 
date    : 2022-03-12 23:03:43 +0900
updated : 2022-03-13 00:23:18 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# PART 01 시스템 

## Unix/Linux
### 사용자 정보 
```sh
$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
```

1. user_account: 사용자 계정명
2. x: 사용자 패스워드(x는 shadow 패스워드를 사용한다는 의미)
3. 0: 사용자 ID(UID)
4. 0: 기본 그룹 ID(GID)
5. root: 사용자 관련 기타 정보(코멘트)
6. /root: 로그인에 성공한 후에 사용자가 위치할 홈 디렉터리 
7. /bin/bash: 로그인 쉘

### 사용자 확인
```sh
$ id
$ id hacker
```

### 패스워드 변경

```sh
$ passwd    /* 로그인한 본인 패스워드 변경 */
$ passwd user   /* root가 사용자 패스워드 변경 */
```

### 그룹 정보
```sh
$ cat /etc/group
root:x:0:root
bin:x:1:root,bin,daemon
```

1. bin: 그룹명
2. x: 그룹의 암호화된 패스워드(사용안함)
3. 1: 기본 그룹 ID(GID)로 그룹명을 대신하는 정수형 숫자
4. root,bin,daemon: 소속된 사용자 계정들


### inode의 속성
- inode nubmer, 파일타입, 접근권한, link count, 소유자 소유그룹, 파일크기,
MAC Time(Last Modification, Accesss, Change Time)


## 프로세스 정보 확인
- ps [-flaAe] [-g egid_list] [-U uid_list] [-u euid_list] [-t terminal_list]
- \-f: 이 옵셜을 사용하면 프로세스 정보가 한 줄씩 출력됨 <br>
(UserName PID PPID C STIME TTY TIME CMD)
- \-l 이 옵션은 -f옵션보다 더 많은 정보를 출력 <br>
(F S UID PID PPID C PRI NI ADDR SZ WCHAN TTY TIME CMD)
- \-a: 최근에 많이 실행된 제어 터미널을 가진 프로세스의 정보를 출력
- \-A, \-e: 현재 시스템에서 실행 중인 모든 프로세스 정보를 출력 


## 사용자가 관리
- 사용자 계정 추가 <br>
useraadd [-option] login_name

```sh
$ useradd test1
```

- 사용자 계정 삭제 <br>
userdel [-r] login_name ( \-r: 사용자의 홈 디렉터리를 삭제)
