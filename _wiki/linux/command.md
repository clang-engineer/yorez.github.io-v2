---
layout  : wiki
title   : 명령어 실행 방법 종류
summary : 
date    : 2021-10-07 10:31:41 +0900
updated : 2022-07-19 13:02:44 +0900
tag     : linux command
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

## ;
성공여부와 상관없이 다음 명령어 실행
```
mkdir test; cd test
```

## &&
앞의 명령어가 성공한 경우만 다음 명령어 실행
 
```
// 이미 test폴더가 있을 경우
// 아래 1. 2. 예시 'mkdir test'명령은 동일하게 실패하지만, 따라오는 명령어 실행 결과는 다름
1. &&으로 연결할 경우
mkdir test && cd test && touch abc (실패, 실행x, 실행x)

2. ;으로 연결할 경우
mkdir test; cd test; touch abc (실패, 실행o, 실행o)
```

## &
명령어를 백그라운드로 동작시킬 때 사용
```
// test 디렉터리 생성과 test이동을 동시에 하려하기 때문에 존재하지 않는 폴더에 이동하려고 하는 것처럼 인식됨(순차 실행 x). 
mkdir test & cd test (성공, 실패)
```

## 명령의 그룹핑
mkdir test 성공했을 경우 {}안의 명령어 그룹을 실행, 실패했을 경우 || 뒤의 명령어를 실행
```
mkdir test && { cd test; touch abc; echo 'success!!' } || echo 'fail to make dir';
```
