---
layout  : wiki
title   : ch01 시스템
summary : 
date    : 2022-03-12 23:03:43 +0900
updated : 2022-03-18 23:02:19 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# PART 01 시스템 

## 패스워드 크래킹 방법 ?
- 사전 공격
- 무차별 공격
- 혼합 공격
- 레인보우 테이블 공격
---
##  /etc/password 파일 구조 ? 
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

---
## 사용자 확인 명령어 ? 
- id [user_account]
```sh
$ id    /* 명령을 실행한 사용자 확인 */
$ id hacker /* hacker 사용자 확인 */
```

---
### 패스워드 변경 명령어 ? 
- passwd [user_account]

```sh
$ passwd    /* 로그인한 본인 패스워드 변경 */
$ passwd user   /* root가 사용자 패스워드 변경 */
```

---
### /etc/grounp 파일 구조? 
```sh
$ cat /etc/group
root:x:0:root
bin:x:1:root,bin,daemon
```

1. bin: 그룹명
2. x: 그룹의 암호화된 패스워드(사용안함)
3. 1: 기본 그룹 ID(GID)로 그룹명을 대신하는 정수형 숫자
4. root,bin,daemon: 소속된 사용자 계정들


---
### 리눅스에서 사용하는 특수문자

---
### 리눅스 파일 시스템 구성 ?
- 부트블럭, 슈퍼블럭, 아이노드 블럭, 데이터 블럭

---
### inode블럭이 가진 속성 ? 
- inode nubmer, 파일타입, 접근권한, link count, 소유자 소유그룹, 파일크기,
MAC Time(Last Modification, Accesss, Change Time)


---
### 링크 생성 ? 

- ln [-s] source_file | source_directory target_file
- 디렉터리는 하드링크가 불가능하다.
 
```sh
$ ln /usr/local/include/mylib.h ~/work/include/mylib.h  /* 하드 링크*/
$ ln -s /usr/local/include ~/work/include   /* 소프트 링크*/
```

---
### ls 명령어 ?
- 명령: ls [-alFR] [file_name | directory_name]
- l: 목록 형태로 디렉터리 및 파일의 정보를 자세히 출력
- a: 도트(.) 파일을 포함하여 디렉터리 내에 있는 모든 디렉터리 및 파일(숨김 포함) 출력
- R: 하위 디랙터리 내용까지 보여줌
- F: 디렉터리인지 어떤 종류의 파일이인지 보여줌 

---
### 접근 권한 변경 명령어?
- 명령: chmod [-R] permission file_name | directory_name 
- R: 하위 디렉터리와 파일의 권한까지 변경
- 해당 파일의 소유주나 슈퍼 유저 roo만 할 수 있음
```sh
$ chmod o-w test.c
$ chmod 664 test.c
```

---
### 소유주 또는 소유그룹 변경
- 명령: chown [-hR] owner [file_name | directory_name], chgrp [-hR] group [file_name | directory_name]
- R: 하위 디렉터리와 디렉터리 하위의 모든 파일의 소유주 변경
- h: 심볼릭 링크와 파일 자체의 소유주나 그룹을 변경


---
### 접근 권한 마스크
- 명령: umask [mask]
- 앞으로 만들어질 파일에 영향을 미치는 명령
- /etc/profile 파일에 umask를 지정하여 시스템 전체 사용자에게 획일적인 umask값을 적용할 수 있음
```sh
$ umask 000 /* umask 값을 000으로 재지정 */
```

---
### 파일 검색
- 명령: find path [expression] [action]
- -name file_name
- -type
- -user uname
- -group gname
- -size [+-]num[단위]
- -perm mode
- -atime [+-]n
- -ctime [+-]n
- -mtime [+-]n
 
--- 
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
