---
layout  : wiki
title   : npm install 설치시 npm ERR! code ERESOLVE
summary : 
date    : 2022-04-19 15:44:43 +0900
updated : 2022-04-19 15:46:29 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# 
npm install 설치시 npm ERR! code ERESOLVE 에러가 발생한다면

npm install 뒤에 '--save --legacy-peer-deps' 를 추가해주면 된다.

```sh
$ npm install --save --legacy-peer-deps
```
