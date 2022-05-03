---
layout  : wiki
title   : git log 출력
summary : 
date    : 2022-03-07 16:48:33 +0900
updated : 2022-05-03 15:25:03 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## Synopsis (git log --help)
```sh
git log [<options>] [<revision range>] [[--] <path>...]
```

## git log -p
각 commit의 diff를 보여줌

## git log -{n}
최근 n개의 결과만 출력

## git log --stat
commit의 통계를 함께 보여줌

## git log --oneline
로그를 한줄로 보여줌

## git log --oneline --graph
로그를 한줄로 그래프 형식으로 보여줌

## git log --oneline --graph --all --decorate
- --all: 모든 브랜치, all을 쓰지 않으면 현재 브랜치만 보여줌
- --decorate: 각 브ㄷ랜치가 어떻게 위치해 있는지(어떤 커밋을 가리키는지 함께 표시)

## git log --graph --pretty=format:'%C(auto)%h%d (%cr) %cn <%ce> %s'
로그에 날짜를 함께 표시 
