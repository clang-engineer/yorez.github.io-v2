---
layout  : wiki
title   : git merge
summary : 
date    : 2022-03-07 13:24:11 +0900
updated : 2022-03-07 13:27:33 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## git commit 없이 병합하기

### —no-commit
일단 병합을 한다음에 병합에 실패한 것으로 가정후 커밋은 하지 않음 
(커밋되지 않은 코드를 스테이지에만 올려놓고 코드를 마지막으로 점검하거나, 리뷰)

## —no-ff
fast-forward 되어질 병합 형태라도 반드시 머지 커밋을 만들어서 병합

```sh
git merge ${commit-hash} --no-commit --no-ff
```

## —squash
현재 브랜치 위에 단일 커밋을 만들어서 브랜치 병합합니다. ( 커밋 합치기 )
```sh
git checkout master
git merge --squash
```
