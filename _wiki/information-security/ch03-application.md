---
layout  : wiki
title   : ch03 어플리케이션
summary : 
date    : 2022-03-27 22:03:52 +0900
updated : 2022-03-28 00:14:49 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# PART 03 어플리케이션

## DNS 동작방식
- /etc/resolv.conf: 시스템 기본 네임서버 설정 정보를 담고 있다.
- /etc/hosts: 네임서버에 질의하기 전에 먼저 참조되는 파일. 도메인/호스트명과 IP주소 매핑 정보를 담고 있다. 
- /etc/host.conf: DNS 질의 순서를 지정하는 파일

## 네임서버 질의/응답 패킷 분석
- 응답 데이터가 512바이트 이하일 경우 UDP(53번 포트) 사용
- 응답 데이터가 512바이트 이상일 경우 TCP(53번 포트) 사용

## DNS Cache 관련 명령어
- ipconfig /displaydns: 로컬 DNS 캐시 정보 조회
- ipconfig /flushdns: 로컬 DNS 캐시 정보 삭제하기

## nslookup 명령어
- nslookup [도메인] [네임서버]

## dig 명령어
- dig [@네임서버] 도메인 [쿼리유형] [질의옵션]

## whois 명령어
- 도메인의 등록 정보(소유정보), 네트워크 할당 정보 등을 조회하기 위한 명령어
- whois [도메인명]: 해당 도메인의 등록정보/소유정보, 네임서버 정보 등을 조회
- whois [IP 주소]: 해당 주소 네트워크 대역을 관리하는 대행자(ISP)정보, 네트워크 할당정보 등을 확인

## DNS 스푸핑 공격
- 스니핑을 이용한 DNS 스푸핑
- DNS 캐쉬 포이즈닝

## DNS 서버 보안
- 재귀적 질의(Recursive Query)에 대한 제한
```sh
allow-recursion {none;};
allow-recursion {127.0.0.1;192.168.56.0/24};
```
- 존 전송(Zone Transfer)에 대한
```sh
allow-transfer {none;};
allow-transfer {192.168.159.137;};
```

## HTTP 쿠키 관련 보안 속성
- httponly 속성: "Set-Cookie 응답 헤더"에서 설정하는 속성으로 클라이언트에서 스크립트를 통해 해당 쿠키에 접근하는 것을 차단
- secure 속성: "Set-Cookie 응답 헤더"에서 설정하는 속성으로 클라이언트에서 HTTPS(SSL/TLS) 통신을 경우에만 해당 쿠키를 전송

## HTTP 응답 주요 상태 코드
- 100: Continue
- 200: OK
- 201: Created
- 202: Accepted
- 301: Moved
- 302: Found
- 304: Not Modified
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

## FTP 보안 취약점
- FTP bounce attack
- TFTP attack
- Anonymous FTP attack

## FTP 접근 제어 설정
- ftpusers 파일을 통한 접근 제어
- TCP Wrapper 를 통한 접근 제어

## SNMP 데이터 수집 방식 341
- Polling 방식: Manager가 Agent에게 정보를 요청하면 응답해주는 방식으로 Agent가 161/UDP 포트를 사용
- Event Reporting 방식: Agent가 이벤트 발생 시 이를 Manager에게 알리는 방식으로 Manager가 162/UDP 포트를 사용

## community string
- SNMP 데몬과 클라이언트가 데이터를 교환하기 전에 인증을 위해 사용하느 인졸읭 패스워드

## 웹서버(Apache) 설정파일(httpd.conf) 주요 내용
- ServerRoot "/etc/httpd": Apache 웹서버의 홈 디렉터리 설정
- PidFile "run/httpd.pid": 웹서버가 기동될 때 자신의 PID를 기록할 파일의 위치 설정
- Listen 80: 웹서버 데몬의 리스닝 포트 지정
- ServerTokens Prod: Apache의 HTTP응답 시 헤더의 Serer 필드를 통해 제공할 서버, OS, 모듈등의 정보 레벨을 지정
- ServerAdmin admin@email.com: 웹문서 로딩 시 에러가 발행했을 경우 에러 페이지에 보일 관리자의 메일 주소
- 
User nobody 
Group nobody
: 서비스를 제공하는 작업 프로세스의 실행 User와 Group 정보를 저장
- Timeout 300: 클라이언트의 요청에 의해 서버와 연결이 된 후 클라이언트와 서버 간에 아무런 메시지가 발행하지 않았을 때 타임아웃 시키고 연결을 끊을 시간을 초단위로 지정
- MaxClients 300: 동시 연결 가능한 클라이언트의 최대 개수
- KeepAlive On: 클라이언트와 연결된 작업 프로세스가 지속적인 요청 작업들을 계속해서 처리할지, 아니면 요청시마다 새로운 작업 프로세스가 처리할지 여부를 결정
- MaxKeepAliveRequest 100: KeepAlive의 값이 On일 경우, 요청 작업의 최대 개수를 지정. 해당 횟수를 초과하면 현재 프로세스는 종료하고 다른 프로세스가 처리.
- KeepAliveTimeout 5: KeepAlive의 값이 On일 경우, 설정한 시간(초 단위)동안 요청이 없다면 해당 프로세스는 연결을 종료. 


## 데이터베이스 보안 통제
- 접근 통제
- 추론 통제
- 흐름 통제

## 데이터베이스 암호화 방식
- 컬럼 암호화 방식 (API 방식, Plug-In 방식)
- 블록 암호화 방식
