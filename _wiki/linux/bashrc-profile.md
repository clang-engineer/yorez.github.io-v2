---
layout  : wiki
title   : /etc/profile, /etc/bashrc, ~/.bash_profile, ~/.bash_rc 
summary : shell 설정 파일에 대해 정리
date    : 2022-07-19 15:53:12 +0900
updated : 2022-07-20 08:30:15 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# 소개
alias를 수정하거나 PATH를 변경할 때 사용되는 설정파일은 조건에 따라 \
/etc/profile, /etc/bashrc, ~/.bash_profile, ~/.bash_rc 로 나뉨.

# Login Shell vs Non Login Shell

## 1. Login Shell
- 쉘을 실행할 때 로그인이 필요한 경우
- ssh로 접속하거나, su 명령어로 들어갈 때
- ex> /etc/profile, ~/.bash_profile

## 2. Non-Login Shell
- 쉘을 실행할 때 로그인이 불필요한 경우
- shell이 실행되는 모든 상황
- ex> /etc/bashrc, ~/.bashrc

# /etc/profile vs ~/.bash_profile

## 1. /etc/profile
- 전역범위 설정 파일. 
- 모든 사용자가 로그인시 실행됨.
- 실행하는 shell 의 종류와 상관없이 실행.

## 2. ~/.bash_profile
- 지역범위 설정 파일. 
- .bash_profile 이 위치하는 홈 경로의 사용자가 로그인 시만 실행.
- bash shell의 경우만 실행.

# /etc/bashrc vs ~/.bashrc

## 1. /etc/bashrc
- 모든 사용자가 shell을 실행시킬 때마다 실행

## 2. ~/.bashrc
- .bashrc 이 위치하는 홈 경로의 사용자가 shell 실행시 실행.

# 사용처
## .bash_profile
- 환경변수 선언

## .bashrc
- 별칭
- 쉘 함수
- 명령 라인의 보완

> https://linuxize.com/post/bashrc-vs-bash-profile/
