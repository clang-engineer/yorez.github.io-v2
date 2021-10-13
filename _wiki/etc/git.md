---
layout  : wiki
title   : git 유용한 명령어 
summary : 
date    : 2021-10-12 09:28:52 +0900
updated : 2021-10-12 16:27:32 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# git 유용한 명령어 정리 

## git diff
### git diff
- commit vs 수정 중인 파일 비교
 
### git diff --cached 
- commit vs add된 파일 비교
 
### git diff HEAD^
- commit vs commit 비교

### git diff {branch1} {branch2}
- branch1 vs branch2 비교

--- 

## git branch
### git branch -r
- 원격 브랜치 목록 보기
 
## git checkout
### git checkout -t {remote branch name}
- 원격 브랜치로 체크아웃

### git chechout -b {local branch name} {remote branch name}
- 원격 저장소와 이름 다르게 하고 싶을 때

---

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
