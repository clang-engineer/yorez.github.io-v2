---
layout  : wiki
title   : npm install err (ex> dependency tree)
summary : 
date    : 2022-07-12 10:52:15 +0900
updated : 2022-07-12 10:58:18 +0900
tags    : 
toc     : true
public  : true
parent  : [[javascript/index]]
latex   : false
---
* TOC
{:toc}

## unable to resolve dependency tree
- npm install 에러 발생시 --force 또는 --legacy 옵션을 사용

```
npm install --force
npm install --legacy-peer-deps
```
 
## --legacy vs --force
--force를 하면 package-lock.json에 몇가지의 다른 의존 버전들을 추가한다.
--legacy를 하면 peerDependency가 맞지 않아도 일단 설치한다.

>> You have the option to retry with --force to bypass the conflict or --legacy-peer-deps command to ignore peer dependencies entirely (this behavior is similar to versions 4-6). - in npm github blog


## 아래와 같이 실행 스크립트에 기본옵션으로 추가도 가능
```sh
"legacy-peer-deps=true" >> .npmrc
```
