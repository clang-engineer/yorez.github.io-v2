---
layout  : wiki
title   : Grep 명령어
summary : 
date    : 2022-07-25 10:22:44 +0900
updated : 2022-07-25 10:50:35 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 	소개
리눅스에서 특정 파일에서 지정한 문자열이나 정규표현식을 포함한 행을 출력해주는 명령어.
tail이나 ls 등 다양한 명령어와 조합하여 응용되는 경우가 많음.
 
## 리눅스 grep 사용법 
grep [옵션][패턴][파일명]
 
### 문자열로 찾기
- 특정 파일에서 'error' 문자열 찾기\
grep 'error' 파일명

- 여러개의 파일에서 'error' 문자열 찾기\
grep 'error' 파일명1 파일명2

- 현재 디렉토리내에 있는 모든 파일에서 'error' 문자열 찾기 \
grep 'error' *

- 특정 확장자를 가진 모든 파일에서 'error' 문자열 찾기 \
grep 'error' *.log

### 정규표현식으로 찾기
- 특정 파일에서 문자열이 포함된 행을 찾기 \
grep '^[ab]' 파일명 

### 특정 파일에서 a로 시작하는 모든 단어를 찾기
- grep 'a*' 파일명 

### 특정 파일에서 a로 시작하고 z로 끝나는 5자리 단어를 찾기
- grep 'a...z' 파일명 

### 특정 파일에서 a,b,c로 시작하는 단어를 모두 찾기
- grep [a-c] 파일명

### 특정 파일에서 apple 또는 Apple로 시작하는 단어를 모두 찾기
- grep [aA]pple 파일명 

### 특정 파일에서 a나 b로 시작되는 모든 행을 찾기
- grep '^[ab]' 파일명 

### 특정 파일에서 apple로 시작되고 0나 9의 숫자로 끝나로 시작되는 모든 행을 찾기
- grep 'apple'[0-9] 파일명

 
## 자주 사용하는 옵션
- -c : 일치하는 행의 수를 출력한다.
- -i : 대소문자를 구별하지 않는다.
- -v : 일치하지 않는 행만 출력한다.
- -n : 포함된 행의 번호를 함께 출력한다.
- -l : 패턴이 포함된 파일의 이름을 출력한다.
- -w : 단어와 일치하는 행만 출력한다.
- -x : 라인과 일치하는 행만 출력한다.
- -r : 하위 디렉토리를 포함한 모든 파일에서 검색한다.
- -m 숫자 : 최대로 표시될 수 있는 결과를 제한한다.
- -E : 찾을 패턴을 정규 표현식으로 찾는다.
- -F : 찾을 패턴을 문자열로 찾는다.
 

## grep의 종류

| 명령어 | 상세                                                              |
|--------|-------------------------------------------------------------------|
| grep   | grep -G (기본값)                                                  |
| egrep  | grep -E / grep --extended-regexp (확장 정규표현식 사용)           |
| fgrep  | grep -F / grep --fixed-string (정규표현식 사용하지 않는다고 선언) |


## 자주 사용되는 예

### 실시간 로그 보기 (tail + grep)
```sh
tail -f mylog.log | grep 192.168.15.86
```
 
### 특정 파일에서 여러개 문자열 찾기
```sh
cat mylog.txt | grep 'Apple' | grep 'Banana'
```

### grep 한 결과 값 txt 파일로 저장하기
```sh
grep -n 'Apple' mylog.txt > result.txt
```

> https://coding-factory.tistory.com/802
> https://www.gnu.org/software/grep/manual/grep.html
