---
layout  : wiki
title   : 모두의 코드 c++
summary : 
date    : 2021-12-15 09:04:12 +0900
updated : 2022-07-02 11:41:18 +0900
tags    : 
toc     : true
public  : true
parent  : [[study/index]]
latex   : false
---
* TOC
{:toc}

# [씹어먹는 c++](https://modoocode.com/135)

c, cpp 레퍼런스를 찾다가 모두의 코드란 개인 웹사이트를 발견 했다. 

모두의 코드에 c, c++ 등의 관련 자료를 무료로 올려주셨는데,

필력과 양질의 코드를 보니 고수의 향기가 물씬낫다... 역시나 약력을 보니 보통분은 아니신 듯 한다.

pdf로도 자료를 올려주셔서 출퇴근 길이나 오며가며 읽기 매우 좋았다..!

3% - 40/982

1.  
    1. [X] 자~ C++의 세계로
    2. [X] 첫 C++프로그램 분석하기
    3. [X] C++은C친구 - C와 공통점
2. [X] C++참조자(레퍼런스)의 도입
3. [X] C++의 세계로 오신 것을 환영합니다. (new, delete)
4. 
    1. [X] 이 세상은 객체로 이루어져 있다. 
    2. [X] 클래스의 세계로 오신 것을 환영합니다. (함수의 오버로딩, 생성자)
    3. [X] 스타크래프트를 만들자1(복사 생성자, 소멸자) 
    4. [X] 스타크래프트를 만들자2(const, static)
    5. [X] 내가 만드는 String 클래스
    6. [X] 클래스의 explicit과 mutable키워드
5. 
    1. [X] 내가만든 연산자 - 연산자 오버로딩
    2. [X] 입출력, 첨자, 타입변환, 증감 연산자 오버로딩
    3. [ ] 연산자 오버로딩 프로젝트 - N차원 배열
6. 
    1. [ ] C++ 표준 문자열 & 부모의 것을 물려쓰자 - 상속
    2. [ ] 가상(virtual) 함수와 다형성
    3. [ ] 가상함수와 상속에 관련한 잡다한 내용들 
7.  
    1. [ ] C++에서의 입출력(istream, ostream)
    2. [ ] C++에서 파일 입출력 - std::ifstream, std::ofstream, std::stringstream
8. 
    1. [ ] Excel 만들기 프로젝트 1부
    2. [ ] Excel 만들기 프로젝트 2부
9. 
    1. [ ] 코드를 찍어내는 틀 - C++ 템플릿(template)  
    2. [ ] 가변 길이 템플릿(Variadic template)
    3. [ ] 템플릿 메타 프로그래밍(Template Meta programming)
    4. [ ] 템플릿 메타 프로그래밍2
10. 
    1. [ ] C++ STL - 백터(std::vector), 리스트(list), 데크(deque)
    2. [ ] C++ STL - 셋(set), 맵(map), unordered_set, unordered_map
    3. [ ] C++ STL - 알고리즘(algorithm)
    4. [ ] C++ 문자열의 모든 것(string과 string_view)
11. C++에서 예외 처리 
12. 
    1. [ ] 우측값 레퍼런스와 이동 생성자 
    2. [ ] Move문법(std::move semantic)과 완벽한 전달(perfect forwarding)
13. 
    1. [ ] 객체의 유일한 소유권 - unique_ptr
    2. [ ] 자원을 공유할 때 - shared_ptr와 weak_ptr
14. 함수를 객체로!(C++ std::function, std::mem_fn, std::bind) 
15. 
    1. [ ] 동시에 실행을 시킨다고? - C++ 쓰레드(thread)
    2. [ ] C++ 뮤텍스(mutex)와 조건 변수(condition variable)
    3. [ ] C++ memory order와 atomic 객체
    4. [ ] C++ future, promise, packaged_task, async
    5. [ ] C++ 쓰레드풀(ThreadPool) 만들기
16. 
    1. [ ] C++유니폼 초기화(Uniform Initialization)
    2. [ ] constexpr와 함께라면 컴파일 타입 상수는 문제없어
    3. [ ] 타입을 알려주는 키워드 decltype와 친구 std::devlval 
17. 
    1. [ ] type_traits 라이르러리, SFINAE, enable_if
    2. [ ] C++ 정규 표현식(<regex>) 라이브러리 소개
    3. [ ] 난수 생성(<random>)과 시간 관련 라이브러리(<chrono>) 소개
    4. [ ] C++ 파일 시스템(<filesystem>) 라이브러리 소개
    5. [ ] C++ 17의 std::optionsal, variant, tuple 살펴보기
18. 초보자를 위한C++강좌 - 쌉어먹는 C++(완결) 
19. 
    1. [ ] Make 사용 가이드(Makefile 만들기)
    2. [ ] C++ 프로젝트를 위한 CMake 사용법
20. 
    1. [ ] 코드 부터 실행 파일까지
    2. [ ] 코드 부터 실행 파일까지 - 컴파일
    2. [ ] 코드 부터 실행 파일까지 - 링킹(Linking)
    4. [ ] 코드 부터 실행 파일까지 - main으로의 여정
21. C++표준 라이브러리에서 자주 쓰이는 패턴 모음






# [[씹어먹는 c]](https://modoocode.com/231)

1. [X] 언어가 뭐야?
2. [X] 
    1. C언어 본격 맛보기 
    2. 주석에 대한 이해
    3. 수를 표현하는 방법(기수법)
3. [X] 변수가 뭐지?
4. [X] 
    1. 계산하러 
    2. 컴퓨터가 수를 표현하는 방법(2의 보수)
5. [X] 문자 입력 받기
6. [X] 만약에...(if문)
7. [X] 뱅글 뱅글(for, while)
8. [X] 우분투 리눅스에서 C프로그래명 하기
9. [X] 만약에...2탄(swich문)
10. [X] 연예인 캐스팅(?) (C언어에서의 형 변환)
11. [X] 
    1. C언어의 아파트(배열), 상수
    2. C언어의 아파트2(고차원의 배열)
12. [X] 
    1. 포인터는 영희이다!(포인터)
    2. 포인터는 영희이다!(포인터)
    3. 포인터는 영희이다!(포인터)
13. [X] 
    1. 마술 상자 함수(function) 
    2. 마술 상자 함수2(function) 
    3. 마술 상자 함수3(function) 
    4. 마술 상자 함수(생각해볼 문제에 대한 아이디어) 
14. [X] 컴퓨터의 머리로 따라가보자 - 디버깅(debugging)
15. [X] 
    1. 일로와봐,문자열(string) 
    2. 일로와봐,문자열(string) - 버퍼에 관한 이해 
    3. 일로와봐,문자열(string) - 문자열 지지고 볶기 & 리터럴
    4. 일로와봐,문자열(string) - 도서 관리 프로젝트
16. [X] 
    1. 모아 모아 구조체(struct) 
    2. 모아 모아 구조체(struct) - 구조체 인자로 가진 함수
    3. 구조체와 친구들(공용체(union), 열거형(enum))
17. [X] 변수의 생존 조건 및 데이터 세그먼트의 구조
18. [X] 
    1. 파일 뽀개기(헤더파일과 #include)
    2. 파일 뽀개기(#친구들, 라이브러리)
19. [X] main함수의 인자, 텅 빈 void형
20. [X] 
    1. 동동동 메모리 동적할당(Dynamin Memory Allocation)
    2. 메도리 동적할당 + 메모리 갖고 놀기
21. [X] 매크로 함수, 인라인 함수 
22. [X] C언어의 잡다한 키워드들(typedef, volatile, #pragma)
23. [X] 
    1. 파일 하고 이야기 하기(파일 입출력에 대한 기본적 이해) 
    2. 파일 하고 이야기 하기(파일 입출력)
    3. 파일 하고 이야기 하기(파일 입출력 - 마무리)
24. [X] 더 빠르게 실행되는 코드를 위하여(C코드 최적화)
