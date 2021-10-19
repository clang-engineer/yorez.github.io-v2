---
layout  : wiki
title   : reset 명령어 메모
summary : 
date    : 2021-10-14 14:59:53 +0900
updated : 2021-10-14 15:16:41 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## git reset <옵션> <commit>
### git reset --mixed
- 기본 옵션
- 변경된 내용 보존 o
- 익덱스 초기화 o 
 
### git reset --soft
- 변경된 내용 보존 o
- 인덱스 초기화 x

### git reset --hard
- 변경된 내용 보존 x
- 익덱스 초기화 o

### git reset HEAD^
- 최신 커밋 1개 취소

### git reset HEAD~n
- n만큼 커밋 취소