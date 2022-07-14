---
layout  : wiki
title   : 디렉토리 별 gitconfig 설정하기
summary : 
date    : 2022-07-14 09:05:55 +0900
updated : 2022-07-14 09:35:17 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## 소개 
회사 <-> 개인 저장소 계정을 구분 짓기 위해 .git/config 를 수정해서 사용자 정보를 변경하는 방법을 사용하고 있었다.
허나, 저장소 별로 일일히 설정 파일을 수정 해야하고 초기화시마다 설정이 삭제되는 문제가 있었다.
검색해보니 디렉토리별 config 를 일괄 관리할 수 있는 방법이 있었고..! 문제가 해결되었다.

## 전역 설정
```sh
git config --global user.name xxx
git config --global user.emal xxx@gmail.com
```

## 디렉터리 설정 추가

- gitconfig 파일은 아래의 설정이 위의 설정을 덮음.
- git directory 가 설정한 패턴과 일치하면, path 에 있는 파일을 include 하도록 추가

### 커스텀 설정파일 생성

~/workspace/company/company.inc
```sh
[user]
    name = customuser
    email = customuser@gmail.com
```
 
### 전역 설정파일(~/.gitconfig) 에 디렉터리 패턴이 일치하면 커스텀 파일로 덮도록 설정
```txt
[user]
    name = xxx
    email = xxx@gmail.com

[includeIf "gitdir:~/workspace/company"]
    path = ~/workspace/company/company.inc
```

## 확인
- 하위 디렉토리를 이동하면서 설정이 제대로 됐는지 확인
```sh
git config --get user.email
```


> 참조: https://til.younho9.dev/log/2021/gitconfig-conditional-include/
