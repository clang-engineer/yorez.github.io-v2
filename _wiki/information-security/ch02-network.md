---
layout  : wiki
title   : ch02 네트워크
summary : 
date    : 2022-03-26 17:08:53 +0900
updated : 2022-03-27 21:57:15 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# PART 02 네트워크

## 스위치 환경에서의 스니핑 공격 기법 ? 148
- 스위치 재밍
- ARP 스푸핑 공격
- ARP 리다이렉트 공격
- ICMP 리다이렉트 공격

## ARP cache table 관련 명령어
- arp -a: 캐쉬 내용보기
- arp -d: 캐쉬 내용삭제
- arp -s: 캐시 정적 설정

## tcpdump IP 단편화 출력 형식 ? 
- frag "단편ID":"단편의크그(IP 헤더 제외)"@"오프셋"+

## IPv4 <-> IPv6 전환 기술 ? 171
- 듀얼스택? <br>IPv4와 IPv6 프로토콜을 동시에 설정하여 통신 상대에 따라 선택적으로 사용할 수 있도록 하는 방식
- 터널링? <br>IPv4 네트워크를 통과하는 가상의 경로를 만들어 통신하는 방식
- 주소변환 또는 헤더 변환? <br> IPv4주소를 IPv6로 변환하거나 IPv6주소를 IPv4 주소로 변환하여 통신하는 방식
 
## ICPM Redirect vs ARP Redirect ? 
- ARP Redirect 는 희생자의 ARP Cache Table 정보를 변조하여 스니핑하는 것이고,
ICMP Redirect는 희생자의 라우팅 테이블을 변조하여 스니핑한다는 차이점이 있다.


## 포트 분류 방식
1. well-know port (0~1023): 잘 알려진 서비스에 의해 예약된 포트
2. registered port (1024~49141): 제조사가 IANA에 용도를 등록해서 사용하는 포트
3. dynamic port (49152~65535): 동적으로 사용하는 포트로 일반적으로 클라이언트 포트로 사용


## ping 명령
-  명령: ping [-c] [-s]
- [-c]: 패킷 정송 횟수 설정
- [-s]: 패킷 크기 설정

## netstat 명령
- -a: 모든 소켓 상태 정보
- -i: 네트워크 인터페이스 정보
- -r: 시스템 라우팅 테이블 정보
- -s: 각 프로토콜별(TCP, UDP, ICMP, IP 등) 통계 정보 
- -t: TCP 소켓을 출력
- -u: UDP 소켓을 출력
- -n: 네트워크 주소를 숫자형식으로 출력하는 옵션
- -p: 해당 소켓의 프로세스명/pid 정보를 출력하는 옵션

## ifconfig 명령
- promiscuous 모드 설정: ifconifig eth1 promisc
- promiscuous 모드 해제: ifconifig eth1 -promisc


## nmap 사용법
- 명령: npm [scan type] [options] <target>
- scan type: -sS, -sT, -sU, -sF, -sX, -sN, -sA, -sP 
- port option: -p [port number]
- output option

## TCP Connect(Open) 스캔
- Open Port: syn -> syn+ack -> ack
- Closed Port: syn -> rst+ack
- Filtered: 응답x or ICMP Destination Unreacheable

## TCP Syn 스캔
- Open Port: syn -> syn+ack -> rst
- Closed Port: syn -> rst+ack
- Filtered: 응답x or ICMP Destination Unreacheable

## TCP FIN/NULL/Xmas 스캔
- Open Port: 응답x
- Closed Port: (FIN/NULL/Xmas) -> rst+ack

## TCP ACK 스캔
- ACK 플래그만 설정해서 보낸다. 방화벽에서 필터링이 된다면 응답이 없거나 ICMP 에러 메시지를 받고 필터링 되지 않으면 RST 응답을 받는다.

## UDP 스캔
- Open Port: UDP응답 or 응답 x
- Closed Port: ICMP Destination Unreachable 응답

## DoS(Denial Of Service) 공격 211
- Ping Of Death Attack
- Land Attack
- Smurf Attack
- Teardrop Attack

## Smurf Attack 대응책?
- 다른 네트워크로부터 자신의 네트워크로 들어오는 Directed Broadcast 패킷을 허용하지 않도록 라우터 설정
- 브로드캐스트 주소로 전송된 ICMP Icho Request 메시지에 대해 응답하지 않도록 시스템 설정

## TCP Syn Flooding 대응책
- 방화벽을 이용하여 동일 Cliet(IP)의 연결(SYN) 요청에 대한 임계치 설정
(ex> iptables -A INPUT -p TCP --dport 80 --syn -m conlimit --conlimit-above 5 -j DROP)
- First SYN DROP 설정
- Backlog quere의 크기를 늘려준다
- SYN+ACK에 대한 대기 시간을 줄인다

## Slow 계열 공격 유형
- Slow HTTP Header DoS(Slowloris) 공격
- Slow HTTP POST DoS(RUDY) 공격
- Slow HTTP Read DoS 공격

## Slow HTTP Header/POST 공격 대응책
- 동시 연결에 대한 임계치 설정을 통한 차단
(ex> iptables -A INPUT -p tcp --dport 80 -m conlimit --conlimit-above 5 -j DROP)
- 연결 타임아웃 설정을 통한 차단

## WEP 암호 방식
- 무작위로 생성하는 24bit 초기벡터(IV)와 고정된 40bit 공유키를 조합하여 WEP암호키를 생성한 후 RC4 암호 알고리즘을 기반으로 한 난수발생기에 입력하여 스트림 암호를 위한 키스림을 생성

## WPA 암호 방식
- RC4-TKIP
- WEP의 24bit 초기벡터(IV)를 확장한 48bit의 초기벡터(IV)를 사용

## WPA2 암호 방식
- AES-CCMP

## IPsec - AH 프로토콜 273
- 전송모드: IP헤더의 전송 중 변경 가능한 필드를 제외한 IP패킷 전체를 인증
- 터널모드: New IP헤더의 전송 중 변경 가능한 필드를 제외한 New IP 패킷 전체를 인증

## IPsec - ESP 프로토콜
- 전송모드: IP 페이로드와 ESP 트레일러를 암호화하고 암호화된 데이터와 ESP 헤더를 인증 
- 터널모드: 원본 IP 패킷 전체와 ESP 트레일러를 암호화하고 암호화된 데이터와 ESP 헤더를 인증
- 인증에 있어서 AH 프로토콜과의 차이점은 AH는 변경 가능한 IP 헤더 필드를 제외한 IP 패킷 전체를 인증하지만 ESP는 IP헤더를 인증하지 않는다.

