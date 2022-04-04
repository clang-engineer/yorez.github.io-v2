---
layout  : wiki
title   : git 관련 추가 팁 
summary : 
date    : 2021-10-21 16:10:42 +0900
updated : 2022-04-04 09:11:38 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

# github에 푸쉬한 후 커밋 되돌리기

## reset
```
git reset --hard head~n
git push -f <원격 저장소 이름> <브랜치 이름>
```


## revert 
### 개별 commit 되돌리기
```
//revert commit이 자동으로 생성o
git revert [되돌리고 싶은 commit의 hash]
```

```
//revert commit이 자동으로 생성x
git revert --no-commit [되돌리고 싶은 commit의 hash]
```

### 통째로 commit 되돌리기


# git commit 날짜 바꾸기
## 마지막 Commit 날짜를 현재 날짜로 설정
```bash
git commit --amend --no-edit --date "$(date)"
```

## 마지막 Commit 날짜를 임의의 날짜로 설정
```bash
git commit --amend --no-edit --date "Mon 20 Aug 2018 20:19:19 KST"
```

## 빈커밋 만들기
```sh
git commit -m "This is a blank commit" --allow-empty
```

## 이력 추적 중이던 내용 무시하기

### file 이력 관리 취소
```bash
git rm --cached <file>
```

### folder 이력 관리 취소
```bash
git rm -r --cached <folder>
```
