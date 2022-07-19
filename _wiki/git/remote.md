---
layout  : wiki
title   : git remote
summary : 
date    : 2022-03-29 16:56:50 +0900
updated : 2022-07-19 13:30:26 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## Synopsis
```sh
git remote [-v | --verbose]
git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=(fetch|push)] <name> <url>
git remote rename <old> <new>
git remote remove <name>
git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
git remote set-branches [--add] <name> <branch>...
git remote get-url [--push] [--all] <name>
git remote set-url [--push] <name> <newurl> [<oldurl>]
git remote set-url --add [--push] <name> <newurl>
git remote set-url --delete [--push] <name> <url>
git remote [-v | --verbose] show [-n] <name>...
git remote prune [-n | --dry-run] <name>...
git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)...]
```

## git remote set-url [주소]
- 원격 저장소 주소 변경하기

## git remote -v
- 원격 저장소 주소 확인하기

##  git 원격 브랜치 삭제하는 방법

```sh
# 방법1. 직접 원격 브랜치를 삭제
git push origin --delete feature/test

# 방법2. 로컬 브랜치를 삭제하고 원격에 동기화
git branch -d feature/test
git push origin feature/test
```
