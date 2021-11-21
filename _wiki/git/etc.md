---
layout  : wiki
title   : git 관련 추가 팁 
summary : 
date    : 2021-10-21 16:10:42 +0900
updated : 2021-11-21 22:04:08 +0900
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
