---
layout  : wiki
title   : 열혈 TCP/IP 소켓 프로그래밍
summary : 
date    : 2021-12-16 08:54:10 +0900
updated : 2021-12-27 10:21:27 +0900
tags    : 
toc     : true
public  : true
parent  : [[study/index]]
latex   : false
---
* TOC
{:toc}

## 열혈 TCP/IP 소켓 프로그래밍

### Part01 네트워크 프로그래밍의 시작

1. [X] 네트워크 프로그래밍과 소켓의 이해
    1. 네트워크 프로그래밍과 소켓의 이해
    2. 리눅스 기반 파일 조작하기
    3. 윈도우 기반으로 구현하기
    4. 윈도우 기반의 소켓관련 함수와 예제
2. [X] 소켓의 타입과 프로토콜의 설정
    1. 소켓의 프로토콜과 그에 따른 데이터 전송 특성
    2. 윈도우 가반에서 이해 및 확인하기
3. [X] 주소체계와 데이터 정렬 
    1. 소켓에 할당되는 IP주소와 PORT 번호
    2. 윈도우 기반에서 이해 및 확인하기
4. [X] TCP 기반 서버/클라이언트1
    1. TCP와 UDP에 대한 이해
    2. TCP기반 서버, 클라이언트 구현
    3. Iterative 기반의 서버, 클라이언트 구현
    4. 윈도우 기반으로 구현하기
5. [X] TCP 기반 서버/클라이언트2 
    1. 에코 클라이언트의 완벽 구현!
    2. TCP의 이록적인 이야기!
    3. 윈도우 기반으로 구현하기
6. [X] UDP 기반 서버/클라이언트
    1. UDP에 대한 이해
    2. UDP기반 서버/클라이언트의 구현
    3. UDP의 데이터 송수신 특성과 UDP에서의 connect 함수호출
    4. 윈도우 기반으로 구현하기
7. [X] 소켓의 우아한 연결종료
    1. TCP기반의 Half-close
    2. 윈도우 기반으로 구현하기
8. [X] 도메인 이름과 인터넷 주소
    1. Domain Name System
    2. IP주소와 도메인 이름 사이의 변환
    3. 윈도우 기반으로 구현하기
9. [X] 소켓의 다양한 옵션
    1. 소켓의 옵션과 입출력 버퍼의 크기
    2. SO_REUSEADDR
    3. TCP_NODELAY
10. [X] 멀티프로세스 기반의 서버구현
    1. 프로세스의 이해와 활용
    2. 프로세세 & 좀비(Zombie) 프로세스
    3. 시그널 핸들링
    4. 멀티태스킹 기반의 다중 접속서버
    5. TCP의 입출력 루틴(Routine) 분할
11. [X] 프로세스간 통신(Inner Process Communication)
    1. 프로세스간 통신의 기본개념 
    2. 프로세스간 통신의 적용
12. [X] IO 멀티플렉싱(Multiplexing)
    1. IO 멀티플렉싱 기반의 서버 
    2. select 함수의 이해와 서버의 구현
    3. 윈도우 기반으로 구현하기
13. [X] 다양한 입출력 함수들
    1. send&recv 입출력 함수
    2. readv&writev 입출력 함수
14. [ ] 멀티캐스트 & 브로드캐스트
    1. 멀티캐스트
    2. 브로드캐스트
    3. 윈도우 기반으로 구현하기

## Part02 리눅스 가반 프로그래밍

15. [ ] 소켓과 표준 입출력
    1. 표준 입출력 함수의 장점
    2. 표준 입출력 함수 사용하기
    3. 소켓 기반에서의 표준 입출력 함수 사용
16. [ ] 입출력 스트림의 분리에 대한 나머지 이야기
    1. 입력 스트림과 출력 스트림의 분리
    2. 파일 디스크립터의 복사와 Half-close
17. [ ] select보다 나은 epoll
    1. epoll의 이해와 활용
    2. 레벨 트리거(Level Trigger)와 엣지 트리거(Edge Trigger)
18. [ ] 멀티쓰레드 기반의 서버구현
    1. 쓰레드의 이론적 이해
    2. 쓰레드의 생성 및 실행
    3. 쓰레드의 문제점과 임계영역
    4. 쓰레드 동기화
    5. 쓰레드의 소멸과 멀티쓰레 기반의 다중접속 서버의 구현
     
## Part03 윈도우 기반 프로그래밍

19. [ ] Windows에서의 쓰레드 사용
    1. 커널 오브젝트(Kernel Objects) 
    2. 윈도우 기반의 쓰레드 생성
    3. 커널 오브젝트의 구 가지 상태
20. [ ] Windows에서의 쓰레드 동기화
    1. 동기화 기법의 분류와 CRITICAL_SECTION 동기화 
    2. 커널모드 동기화 기법
    3. 윈도우 기반의 멀티 쓰레드 서버 구현
21. [ ] Asynchronous Notification IO 모델 
    1. 비동기(Asynchronous Notification IO) 모델의 이해
    2. 비동기(Asynchronous Notification IO) 모델의 이해와 구현
22. [ ] Overlapped IO 모델 
    1. Overlapped IO 모델의 이해
    2. Overlapped IO에서의 입출력 완료의 확인
23. [ ] IOCP(Input Output Completion Port) 
    1. Overlapped IO를 기반으로 IOCP 이해하기 
    2. IOCP의 단계적 구현

## Part04 네트워크 프로그래밍 마무리하기

24. [X] HTTP 서버 제작하기
    1. HTTP(Hypertext Transfer Protocol)의 개요 
    2. 매우 간단한 웹 서버의 구현
25. [X] 앞으로 해야 할 것들 
    1. 네트워크 프로그래밍! 얼마나 공부해야 하나요?
    2. 네트워크 프로그래밍 관련 책 소개
