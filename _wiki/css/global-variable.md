---
layout  : wiki
title   : 전역변수
summary : 
date    : 2022-03-18 14:38:36 +0900
updated : 2022-03-18 15:11:23 +0900
tags    : 
toc     : true
public  : true
parent  : [[css/index]]
latex   : false
---
* TOC
{:toc}

## 소개
css도 지역변수, 전역변수 같은 개념이 있다. 
- 지역변수: 자신의 부모 엘리먼트에 선언된 변수에만 접근할 수 있다.
- 전역변수: 모든 엘리먼트에서 접근 가능하다.
 
## 방법
- :root 가상 선택자를 이용한다. 
- :root는 최상위 엘리먼트인 html와 동일하다. 허나, html태그 이름을 선택자로 쓰면 우선순위에서 1점 밖에 부여되지 않는다. (:root 가상 선택자는 class로 간주되어 10점이 부여된다.)
때문에, css에서 변수를 선언할 때는 :root라는 가상선택자를 이용해 최상위 엘리먼트에 선언하여 모든 엘리먼트에서 변수를 사용할 수 있도록 하는 것이 보편적이다. (ex> 부트스트랩)

## 예시

### 선언
```css
:root {
    --red : #DC3545;
    --blue: #007bff;
    --indigo: #6610f2;
    --purble: #6f42c1;
    ...
}
```

### 참조방법
1. 단순 사용
```css
div { 
    background-color: var(--red); 
}
```

2. 변수값이 유효하지 않은 경우
```css
div {
    background-color: var(--red, #F00);
}
```

3. 변수값이 유효하지 않은 경우 다른 변수를 적용 할 때
```css
div {
    background-color: var(--red, var(--blue, #F00));
}
```

4. CSS 변수를 적용할 수 없을 때 방어코드 (ex>익스플로러)
```css
div {
    background-color: #F00;
    background-color: var(--red, #F00);
}
```
