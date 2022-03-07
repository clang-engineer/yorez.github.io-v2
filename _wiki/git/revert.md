---
layout  : wiki
title   : git revert
summary : 
date    : 2021-10-23 17:35:34 +0900
updated : 2022-03-07 17:07:34 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## Synopsis (git revert --help)
```sh
git revert [--[no-]edit] [-n] [-m parent-number] [-s] [-S[<keyid>]] <commit>...
git revert (--continue | --skip | --abort | --quit)
```

https://www.lainyzine.com/ko/article/git-revert-reverting-commit-in-git-repository/

## 되돌리고 커밋 직접 작성하기
git revert [COMMIT_ID] -e
git revert [COMMIT_ID] --edit

## 되돌리고 커밋 메시지 따로 수정하고 싶지 않을 때
git revert [id] --no-edit

## 바로 직전에 커밋한 내용 되돌리기
git revert HEAD

## 특정 커밋의 내용을 되돌리는 방법
git revert [COMMIT_ID]: 

### 여러 커밋을 한번에 되돌리는 법
git revert --no-edit [커밋 1id] [커밋 2id]
--> 1, 2순으로 각각 리버트 커밋이 만들어짐

### 여러 커밋을 되돌리지만 카밋은 하나로
git revert -n adf03568 3cdce394
>>돌린 내용이 한꺼번에 index에 방영되지만 커밋x

'''
git revert --continue
# EDITOR로 커밋 메시지 작성
'''

### 머지 커밋(Merge commit)을 되돌리는 방법
'''
//머지가 무슨 커밋을 병합했는지 확인
git show [merge commit id]

git revert -m 1 [merge commit id]
git revert -m 2 [merge commit id]
'''
병합 커밋 중 어느쪽으로 돌아갈지 선택해야함
