---
layout  : wiki
title   : diff 명령어 메모 
summary : 
date    : 2021-10-14 14:44:37 +0900
updated : 2022-03-07 17:05:43 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## Synopsis (git diff --help)
```sh
git diff [<options>] [<commit>] [--] [<path>...]
git diff [<options>] --cached [--merge-base] [<commit>] [--] [<path>...]
git diff [<options>] [--merge-base] <commit> [<commit>...] <commit> [--] [<path>...]
git diff [<options>] <commit>...<commit> [--] [<path>...]
git diff [<options>] <blob> <blob>
git diff [<options>] --no-index [--] <path> <path>
```

## git diff
- commit vs 수정 중인 파일 비교
 
## git diff --cached 
- commit vs add된 파일 비교
 
## git diff HEAD^
- commit vs commit 비교

## git diff {branch1} {branch2}
- branch1 vs branch2 비교
