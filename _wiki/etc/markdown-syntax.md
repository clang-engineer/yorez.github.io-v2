---
layout  : wiki
title   : 유용한 마크다운 문법
summary : 
date    : 2021-10-13 15:22:37 +0900
updated : 2021-10-13 16:50:14 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# 유용한 마크다운 문법

## code block
### 특정 언어를 명시하면 syntax 하이라이팅
````
```c
int val = 10;
printf(%s,"Hello, World!");
```
````

### backtick 중첩으로 마크다운 코드블록 표현
`````
````
```
본문
```
````
`````

---
## 주석
### \\\\<\!-- & -->
```
\\<!-- 와 -->로 감싸주면 <!-- 주석처리 -->
```

---
## 링크
### 인라인 링크
```
[Google](http://www.google.co.kr"구글")
```

### 참조 링크
```
검색엔진은 [Google][1] 이 있다.
(…본문…)
[1]: http://google.com/ “구글”
```

### url 링크
```
<http://www.google.co.kr>
```

---
## Text 강조
### 기울여쓰기
```
* or _
ex> *test* or _test_
```
 
### 굵게 쓰기
```
** or __
ex> **test** or __test__
```

### 기울여 +  굵게 쓰기
```
*** or ___
ex> ***test*** or ___test___
```


---
## 표
### 정렬

**:** 로 **정렬기준** 추가

```
| Header One | Header Two | Header Three | Header Four |
| ---------- | :--------- | :----------: | ----------: |
| Default    | Left       | Center       | Right       |
```

| Header One | Header Two | Header Three | Header Four |
| ---------- | :--------- | :----------: | ----------: |
| Default    | Left       | Center       | Right       |


### 열 병합
```
| Column 1 | Column 2 | Column 3 | Column 4 |
| -------- | :------: | -------- | -------- |
| No span  | Span across three columns    |||
```

| Column 1 | Column 2 | Column 3 | Column 4 |
| -------- | :------: | -------- | -------- |
| No span  | Span across three columns    |||


---
### 목차 생성하기
문서 내에 \{:toc}는 목차를 자동 생성한다

```
{:toc}
```
