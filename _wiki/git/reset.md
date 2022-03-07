---
layout  : wiki
title   : reset 명령어 메모
summary : 
date    : 2021-10-14 14:59:53 +0900
updated : 2022-03-07 17:06:52 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## git reset <옵션> <commit>

## Synopsis (git reset --help)
```sh
git reset [-q] [<tree-ish>] [--] <pathspec>...
git reset [-q] [--pathspec-from-file=<file> [--pathspec-file-nul]] [<tree-ish>]
git reset (--patch | -p) [<tree-ish>] [--] [<pathspec>...]
git reset [--soft | --mixed [-N] | --hard | --merge | --keep] [-q] [<commit>]
```
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
 
### 특정 파일만 취소하고 싶을 때
-- git checkout -- [Filename]

