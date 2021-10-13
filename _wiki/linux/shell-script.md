---
layout  : wiki
title   : 유용한 shell script 
summary : 
date    : 2021-10-13 12:57:35 +0900
updated : 2021-10-13 12:59:57 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# 유용한 shell script

## java Jar 파일을 백그라운드로 실행
```
#!/bin/sh
nohup java -jar xxx.jar &
```
