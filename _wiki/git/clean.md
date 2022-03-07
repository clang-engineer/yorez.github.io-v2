---
layout  : wiki
title   : git clean 명령어
summary : 
date    : 2021-10-21 16:13:12 +0900
updated : 2022-03-07 17:05:07 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## Synopsis (git clean --help)
```sh
git clean [-d] [-f] [-i] [-n] [-q] [-e <pattern>] [-x | -X] [--] <path>...
```

## 디렉터리를 제외한 파일들만 삭제
```sh
$ git clean -f 
```

## 디렉터리까지 삭제
```
$ git clean -f -d
```

## ignored 된 파일까지 삭제
$ git clean -f -d -x
