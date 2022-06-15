---
layout  : wiki
title   : reset 명령어 메모
summary : 
date    : 2021-10-14 14:59:53 +0900
updated : 2022-06-15 09:06:07 +0900
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
 
### 특정 파일만 add를 취소하고 싶을 때
```sh
git checkout -- [filename]
```

### 특정 파일을 되돌리고 싶을 때
```sh
// HEAD 대신 다른 커밋 SHA-1 체크섬 값을 입력하면 해당 커밋 시점으로 되돌림
// '--' 이 git checkout 명령에 뒤따라 오는 것이 파일이라는 것을 나타냄 
// ('--' 이 없다면 파일 이름이 브랜치 이름과 같을 경우 해당 브랜치로 체크아웃하거나, 특정 커밋 시점으로 저장소 전체가 돌아갈수 있음)
// git reset 명령의 hard 옵션과 유사
git checkout HEAD -- [filename]
```
