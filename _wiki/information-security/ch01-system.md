---
layout  : wiki
title   : ch01 시스템
summary : 
date    : 2022-03-12 23:03:43 +0900
updated : 2022-03-21 01:12:12 +0900
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
7. /bin/bash: 로그인 쉘(* 로그인이 불필요한 계정"/sbin/nologin" 또는 "/bin/false")

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
- -type (f:일반파일, d:디렉터리, b:블럭장치파일, c:문자장치파일, l:심볼릭링크파일, s:유닉스도메인소켓, p:파이프)
- -user uname
- -group gname
- -size [+-]num[단위]
- -perm mode
- -atime [+-]n
- -ctime [+-]n
- -mtime [+-]n

---
### 프로세스 제어 블럭(PCB: Process Control Block)에 포함된 정보
- 프로세스 상태: 프로세스의 현재 상태정보를 저장
- 프로세스 번호: 프로세스를 식별하기 위한 번호
- 프로그램 카운터: 문맥교환이 발생할 경우 다음에 실행할 명령어의 위치값을 저장
- 레지스터: 문맥교환이 발생할 경우 현재 프로세스의 실행 상태정보(레지스터 정보)를 저장
- 메모리 정보: 프로세스가 사용하는 메모리 page 혹은 또는 segment 테이블 정보
 
--- 
## 프로세스 정보 확인
- ps [-flaAe] [-g egid_list] [-U uid_list] [-u euid_list] [-t terminal_list]
- \-f: 이 옵션을 사용하면 프로세스 정보가 한 줄씩 출력됨 <br>
(UserName PID PPID C STIME TTY TIME CMD)
- \-l 이 옵션은 -f옵션보다 더 많은 정보를 출력 <br>
(F S UID PID PPID C PRI NI ADDR SZ WCHAN TTY TIME CMD)
- \-a: 최근에 많이 실행된 제어 터미널을 가진 프로세스의 정보를 출력
- \-A, \-e: 현재 시스템에서 실행 중인 모든 프로세스 정보를 출력 


---
### ps -ef 실행 결과 해석
- UID: User ID, 프로세스의 EUID(Effective User ID)
- PID: Process ID
- PPID: Parent Process ID
- C: 프로세스 스케줄링을 우한 CPU 사용량(현재 사용되지 않음)
- STIME: Start TIME, 프로세스가 시작된 시간을 의미("월, 일" 또는 "시:분:초" 형식)
- TTY: 프로세스와 연결될 터미널 타입. "?"는 제어 터미널에 연결되어 있지 않음을 의미
- TIME: CPU 사용 시간으로 "시:분" 형식으로 표현
- CMD: 프로세스명

---
### 프로세스 간 통신(시그널)
- kill [-signal_number | -signal_name] PID 
- kill -l [signal]
- -signal_number | -signal_name: 시그널 번호 또는 시그널명(SIG는 생략)이다.
- -l: 지원 가능한 시그널 목록을 출력한다.

---
### 사용자 계정 추가
- useraadd [-option] login_name
```sh
$ useradd test1
```
- 슈퍼 유저 root만 사용할 수 있다

--- 
### 사용자 계정 삭제
- userdel [-r] login_name 
- -r: 사용자의 홈 디렉터리를 삭제
- 슈퍼 유저 root만 사용할 수 있다

---
### 그룹 추가
- groupadd [-g gid] group_name
- -g gid: 새로운 그룹에 할당할 그룹의 GID를 명시적으로 지정한다.
```sh
$ groupadd study
$ groupadd -g 100 study /* GID 100인 study 그룹을 새로 추가한다.*/
```

---
### 그룹 삭제
- groupdel group_name

---
### 하드디스크 사용량 확인 57
- du [-option] [directory_name]
- -a: 디렉터리뿐만 아니라 하위의 파일에 대한 정보도 보여준다.
- -s: 현재 디렉터리가 차지하는 총용량만 출력한다.
- -k: 사용량을 킬로바이트 단위로 환산하여 출력한다.
- -h: 사용자가 이해하기 쉬운 용량의 단위(KB,MB,GB)를 표시(1M를 1,048,576단위로 계산)

---
### crontab 파일 명령어 60
- crontab [-u user] [-e | -l | -r]
- -e: crontab 파일을 편집한다.
- -l: crontab 피일을 출력한다.
- -r: crontab 파일을 삭제한다.
- 사용자 계정을 명시하지 않으면 자신의 계정을 의미한다.
```sh
$ crontab -u test -e
$ crontab -u test -l
$ crontab -u test -r
$ crontab -e  
$ crontab -l
$ crontab -r
```
 
---
### crontab 파일의 구조
- 필드1 - 분, 분은 0-59까지의 숫자로 기술한다.
- 필드2 - 시, 시는 0-23까지의 숫자로 기술한다.
- 필드3 - 일, 일은 1-31까지의 숫자로 기술한다.
- 필드4 - 월, 월은 1-12까지의 숫자로 기술한다.
- 필드5 - 요일, 요일은 0-6까지의 숫자로 기술한다.(0: 일요일)
- 필드6 - 작업, 지정 시간에 실행할 작업을 절대 경로로 기술하고 필요한 옵션 및 인수를 함께 나열한다.


---
### /etc/protocols, /etc/services 파일
1. /etc/protocols 파일
- 인터넷상에서 사용하는 프로토콜과 프로토콜 식별 번호를 정의해 놓은 파일로 IANA(Internet Assigned Number Authority) 기구를 통해 관리된다
2. /etc/services 파일
- 인터넷상에서 사용하는 다양한 서비스에 대한 포트/프로토콜 정보를 정의해 놓은 파일로 IANA(Internet Assigned Number Authority) 기구를 통해 관리된다.
- well-known port(0-1023), registered port(1024-49151), dynamic port(49152-65535) 정보를 확인할 수 있다.

---
### TCP Wrapper 71
- /etc/hosts.allow와 /etc/hosts.deny 파일에 정의된 호스트 정보(IP 정보)를 기준으로 외부로부터 접근을 선택적으로 제한할 수 있다.
- 먼저 host.allow파일을 참조하여 해당 호스트 정보가 있다면 접근을 허용한다. 없다면 hosts.deny 파일을 참조하여 해당 호스트 정보가 있으면 접근을 차단한다.
hosts.deny 파일에도 해당 호스트 정보가 없다면 default로 모든 접근을 허용한다.
- 문법: service_list: client_list [: shell_command]

| host.deny | hosts.allow                                    | 설명                                                                                     |
|-----------|------------------------------------------------|------------------------------------------------------------------------------------------|
| ALL : ALL | ALL : 192.168.1.1                              | 192.168.1.1번 IP주소에 대해 모든 서비스가 이용 가능하다.                                 |
| ALL : ALL | in.telnetd : .algisa.co.kr                     | algisa.co.kr 도메인에 속한 모든 호스트는 Telnet 서비스가 가능하다.                       |
| ALL : ALL | ALL : 192.168.1.0 / 255.255.255.0              | 192.168.1.0(~192.168.1.255) 네트워크에 속한 모든 호스트는 모든 서비스가 가능하다.        |
| ALL : ALL | ALL : 192.168.1.                               | 192.168.1로 시작하는 IP주소를 갖는 모든 호스트는 Telnet 서비스가 가능하다.               |
| ALL : ALL | ALL : LOCAL                                    | 같은 네트워크에 있는 모든 호스트에 대해 모든 서비스가 가능하다.                          |
| ALL : ALL | ALL EXCEPT in.telnetd : ALL                    | 모든 호스트에 대해 Telnet 서비스를 제외한 모든 서비스가 가능하다.                        |
| ALL : ALL | in.telnetd : .algisa.com EXCEPT www.algisa.com | www.algisa.com을 제외한 algisa.com 도메인의 모든 호스트에 대해 Telnet 서비스가 가능하다. |

---
### TCP Wrapper을 사용하기 전과 후의 Telnet 서비스에 대한 /etc/inetd.conf 파일 구조
| 구분   | 서비스 | 소켓 타입 | 프로토콜 | 플래스 | 사용자 | 실행경로             | 실행인수   |
|--------|--------|-----------|----------|--------|--------|----------------------|------------|
| 사용전 | Telnet | stream    | TCP      | nowait | root   | /usr/sbin/in.telnetd | in.telnetd |
| 사용후 | Telnet | stream    | TCP      | nowait | root   | /usr/sbin/tcpd       | in.telnetd |
- TCP Wrapper를 사용할 경우 해당 서비스의 실행경로에 "usr/sbin/tcpd"를 명시한다. 
inetd 데몬은 외부로부터 서비스 요청이 올 경우 inetd.conf 파일을 참조하여 실행경로에 설정된 /user/sbin/tcpd(TCP Wrapper 프로세스)를 실행한다.
- tcpd는 hosts.allow 및 hosts.deny 파일을 참조하여 접근제어를 수행한 후 실행인수로 설정된 서비스를 실행한다. 


---
### 슈퍼 데몬[xinetd]
- 기존의 inetd 슈퍼데몬의 비효율적인 리소스 관리와 보안성 문제를 극복하기 위해 나온 슈퍼데몬으로 서비스별 다양한 설정 옵션을 자기고 있다.
- /etc/xinetd.conf: 글로벌 xinetd 설정파일
- /etc/xinetd.d/서비스 설정파일: 개별 서비스에 대한 설정파일
- service: 서비스 이름
- disables: 해당 서비스의 실행 여부를 결정한다. yes / no
- socket_type: 서비스 소켓 유형을 설정한다. 일반적으로 tcp 의 경우 stream, udp의 경우 dgram을 설정한다.
- wait: 서비스 요청 처리 중 다음 요청이 들어오면 이를 즉시 처리할 것인지(no) 이전 요청이 완료될 때가지 대기할 것인지(yes)를 설정한다.
- user: 어떤 사용자로 서비스를 실행할지 설정한다.
- server: 서비스 실행 파일 경로를 설정한다. 반드시 절대 경로로 설정한다.
- cps(connection per second): 연결 요청을 제한하기 위한 설정으로 첫 번째 인자는 초당 연결 개수를 의미하고 두 번째 인자는 초당 연결 개수를 초과하면 일시적으로 서비스가 중지되는데 서비스 일시 중지 후 재시작할 때까지
대기하는 시간을 의미한다.
- instances: 동시에 서비스할 수 있는 서버의 최대 개수를 지정한다.
- per_source: 출발지 IP를 기준으로 최대 서비스 연결 개수를 지정한다.
- only_from: 특정 주소 또는 주소 대역만 접근을 허용한다.
- no_access: 특정 주소 또는 주소 대역의 접근을 차단한다.
- access_time: 지정한 시간 범위 내에서만 접근을 허용한다.
- log_on_failure: 서버 접속에 실패했을 경우 로그파일에 기록할 내용을 설정한다. 
- log_on_access: 서버 접속에 성공했을 경우 로그파일에 기록할 내용을 설정한다.    


---
### root 계정의 권격 접속 제한
1. /etc/pam.d 디렉터리에 있는 remote 서비스 설정파일에 아래와 같이 pam_securetty.so 모듈을 추가한다.
2. /etc/securetty 파일에 'pts/~' 터미널을 모두 제거한다.
    - tty(terminal-teletype): 서버와 연결된 모니터, 키보드 등을 통해 사용자가 콘솔로 직접 로그인함
    - pts(pesudo-terminal): Telnet, 터미널 등을 통해 접속하는 가상 터미널을 의미

---
### SSH(Secure Shell) root 원격 접속 제한 설정 
- SSH데몬 설정 파일인 sshd_config(/etc/ssh/sshd.config)의 PermitRootLogin 항목을 no로 설정하여 root 계정의 원격 접속을 허용하지 않도록 한다.


---
### 계정 잠금 임계값 설정
- /etc/pam.d 디렉터리에 있는 system-auto 서비스 설정파일에 아래와 같이 추가한다.
```sh
#cat /etc/pam.d/system-auth
auth required /lib/security/pam_tally.so deny=5 unlock_tiem=120 no_magic_root
account required /lib/security/pam_tally.so no_magic_root reset
```
- no_magic_root: root 계정은 패스우드 잠금 설정을 적용하지 않는다.
- reset: 접속 시도 성공 시 실패한 횟수 초기화

---
### root 계정 su 제한 81
- pam_wheel.so 모듈 이용
- wheel 그룹(su 명령어 사용그룹)에 su명령어를 사용할 사용자를 추가한다.

---
### sudo 명령어를 이용한 관리자(root) 권한 부여
- su 명령을 사용할 경우 관리자(root)의 비밀번호를 알려줘야 한다는 부담이 있으며, 최소 권한의 원칙에 따라 관리자로 로그인하는 것을 차단하고 
필요한 경우에만 sudo 명령을 사용하여 제한적으로 관리자 권한의 명령어를 실행하는 것을 보안 관점에서 권장한다.
- 설정 파일: sudoers(/etc/sudoers)
- 문법: sudo [-u 실행 권한 계정명] 명령어
- -u: 명령어를 실행알 때 가질 권한의 계정명, 생략시 root 권한을 실행 권한으로 가진다.

#### sudoers 파일
```
계정명 호스트명=(실행 권한 계정명) [NOPASSWD:]명령어
```
- 계정명: sudo 명령을 실행할 계정명이나 그룹명, 그룹명을 줄 경우에는 '%그룹명'을 사용하고 모두에게 줄 경우에는 'ALL' 지정
- 호스트명: sudo 명령을 실행할 호스트의 호스트명 또는 IP, 모든 서버가 대상이면 'ALL' 지정
- 실행 권한 계정명: 명령어를 실행할 때 가질 권한의 계정명, root를 포함한 모든 계정의 권한을 부여할 경우 'ALL'로 지정하며 생략시 'root'권한 부여
- NOPASSWD: 해당 옵션을 설정할 경우 sudo 명령을 실행하는 계정의 비밀번호를 물어보지 않는다.
- 명령어: 실행을 허용할 명령어의 경로. 모든 명령어를 허용할 경우 'ALL' 지정
