---
layout  : wiki
title   : branch  명령어 메모
summary : 
date    : 2021-10-14 14:58:44 +0900
updated : 2021-11-18 08:59:20 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]] 
latex   : false
---
* TOC
{:toc}

## git branch
### Synopsis
```sh
git branch [--color[=<when>] | --no-color] [--show-current]
        [-v [--abbrev=<n> | --no-abbrev]]
        [--column[=<options>] | --no-column] [--sort=<key>]
        [--merged [<commit>]] [--no-merged [<commit>]]
        [--contains [<commit>]] [--no-contains [<commit>]]
        [--points-at <object>] [--format=<format>]
        [(-r | --remotes) | (-a | --all)]
        [--list] [<pattern>...]
git branch [--track | --no-track] [-f] <branchname> [<start-point>]
git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branchname>]
git branch --unset-upstream [<branchname>]
git branch (-m | -M) [<oldbranch>] <newbranch>
git branch (-c | -C) [<oldbranch>] <newbranch>
git branch (-d | -D) [-r] <branchname>...
git branch --edit-description [<branchname>]
```
### git branch -r
- 원격 브랜치 목록 보기
 
## git checkout
### git checkout -t {remote branch name}
- 원격 브랜치로 체크아웃

### git chechout -b {local branch name} {remote branch name}
- 원격 저장소와 이름 다르게 하고 싶을 때

## 브랜치 이름 변경하기
### git branch -m \<oldname\> \<newname\>
- 브랜치 이름변경 기본 문법

### git branch -m \<newname\>
- 현재 브랜치 이름 변경


## git branch -d \<local branch name\>
- local branch 삭제
 
## 원격 브랜치 삭제
- 원격에서 삭제하고 싶은 타겟 브랜치 이름을 **feature/test**라고 가정
 
### 방법1 - 직접 원격 브랜치를 삭제
```git
git push origin --delete feature/test
```

## 방법2 - 로컬 브랜치를 삭제하고 원격에 동기화
```git
git branch -d feature/test
git push origin feature/test
```
