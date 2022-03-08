---
layout  : wiki
title   : cpu 사용량 확인
summary : 
date    : 2022-03-08 09:51:11 +0900
updated : 2022-03-08 10:02:07 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 1. mpstat
```sh
# 사용률 %로 표시
mpstat | tail -1 | awk '{print 100-$NF}'
```

## 2. top
```sh
# 사용률 %로 표시
top -b -n1 | grep -Po '[0-9.]+ id'
# 남는 사용률 %로 표시
top -b -n1 | grep -Po '[0-9.]+ id' | awk '{print 100-$1}'
```
