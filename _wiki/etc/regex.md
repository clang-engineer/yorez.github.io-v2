---
layout  : wiki
title   : regex 
summary : 
date    : 2021-10-08 10:01:58 +0900
updated : 2021-10-08 13:40:46 +0900
tag     : regex
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# 정규표현식 정리

> https://regexr.com/

## Character classes
### .
- 줄바꿈을 포함한 모든 문자

### \w \d \s
- 문자, 숫자, 공백

### \W \D \S 
- 문자, 숫자, 공백이 아닌 것

### [abc]
- a, b, c 중에 포함된 문자

### [^abc]
- a, b, c 중에 포함되지 않은 문자

### [a-g]
- a-g 중에 포함된 문자

--- 
## anchors
### ^abc$
- 문장의 시작 또는 끝

### \b \B
- 단어의 끝 또는 시작

---
## escaped characters
### \. \* \\
- 특수문자

### \t \n \r
- 탭, 개행문자

---
## Groups & Lookaround
### (abc)
- 문자를 그룹화하고 패턴을 캡처

### \1
- 첫번째로 캡처된 그룹을 참조

### (?:abc)
- 문자를 그룹화하나 캡처하지 않음 

### (?=abc)
- 그룹 문자를 포함한 문자열을 찾으나 해당영역을 선택하지 않음

### (?!abc)
- 그룹 문자를 포함하지 않는 문자열을 찾으나 해당영역을 선택하지 않음


---
## Quantifiers & Alternation
### a* a+ a?
- 0 또는 이상, 1 또는 이상, 0 또는 1  

### a{5} a{2,}
- 정확히 5, 2이상

### a{1,3}
- 1에서 3사이

### a+? a{2,}?
- 가능한 적게 일치하는 패턴

### ab | cd
- ab이거나 cd
