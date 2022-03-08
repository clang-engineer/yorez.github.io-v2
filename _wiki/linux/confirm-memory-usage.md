---
layout  : wiki
title   : 메모리 사용량 확인
summary : 
date    : 2022-03-08 10:07:45 +0900
updated : 2022-03-08 10:09:53 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

## 1. sar
```sh
sar -r 1
```

## 2. free
```sh
free
```

## 3. top
```sh
top -n1 | grep Mem
```

## 4. meminfo
```sh
cap /proc/meminfo | grep Mem
```
