---
layout  : wiki
title   : git stash 정리
summary : 
date    : 2021-10-21 12:47:09 +0900
updated : 2022-03-07 17:07:45 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}


### Synopsis (git stash --help)
```sh
git stash list [<log-options>]
git stash show [-u|--include-untracked|--only-untracked] [<diff-options>] [<stash>]
git stash drop [-q|--quiet] [<stash>]
git stash ( pop | apply ) [--index] [-q|--quiet] [<stash>]
git stash branch <branchname> [<stash>]
git stash [push [-p|--patch] [-k|--[no-]keep-index] [-q|--quiet]
	     [-u|--include-untracked] [-a|--all] [-m|--message <message>]
	     [--pathspec-from-file=<file> [--pathspec-file-nul]]
	     [--] [<pathspec>…​]]
git stash clear
git stash create [<message>]
git stash store [-m|--message <message>] [-q|--quiet] <commit>
```

## git stash, git stash save
- 새로운 stash를 스택에 만들어 하던 작업을 임시로 저장
- working director가 깨끗해짐
 
## git stash list
- 저장한 stash 목록 확인

## git stash apply
- 가장 최근의 stash를 가져와 적용.
- git stash apply [stash 이름]을 통해 가져오고 싶은 stash를선택
- git stash apply --index 을 통해 staged 상태까지 복원

## git stash drop
- 스택에 남아 있는 stash 제거
- git stash drop [stash 이름]을 통해 제거하고 싶은 stash를 선택

## git stash pop
- apply + drop
- 적용과 동시에 스택에서 해당 stash 제거

## git stash show -p | git apply -R
- 잘못 stash 적용한 것을 돌리고 싶을 때
- 가장 최근의 stash를 사용하여 패치를 만들고 그것을 거꾸로 적용.


### TIP alias로 편리하게 사용하자.
stash-unapply라는 명령어를 등록하여 간단하게 사용할 수 있다.
```shell
$ git config --global alias.stash-unapply '!git stash show -p | git apply -R'
$ git stash apply
$ #... work work work
// alias로 등록한 stash 되돌리기 명령어
$ git stash-unapply
```
