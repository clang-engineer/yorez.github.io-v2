---
layout  : wiki
title   : 원격 브랜치 삭제하기
summary : 
date    : 2021-11-03 11:58:25 +0900
updated : 2021-11-03 12:05:10 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

# git 원격 브랜치 삭제하는 방법
### 원격에서 삭제하고 싶은 타겟 브랜치 이름을 **feature/test**라고 가정
## 방법1
### 직접 원격 브랜치를 삭제
```git
git push origin --delete feature/test
```

## 방법2
### 로컬 브랜치를 삭제하고 원격에 동기화
```git
git branch -d feature/test
git push origin feature/test
```
