---
layout  : wiki
title   : ch01 시스템
summary : 
date    : 2022-03-12 23:03:43 +0900
updated : 2022-03-12 23:25:34 +0900
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
