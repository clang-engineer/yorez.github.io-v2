---
layout  : wiki
title   : stack edit 소개
summary : 
date    : 2021-10-05 08:57:35 +0900
updated : 2021-10-05 12:59:38 +0900
tags    : stack edit
toc     : true
public  : true
parent  : [[/etc/index]]
latex   : false
---
* TOC
{:toc}


# Stack Edit 

주소 : [https://stackedit.io](https://stackedit.io/)

markdown을 web 에서 편리하게 편집하게 도와주는 site.
개인 계정을 생성하고 문서를 관리할 수 있다. 
직접 사이트에 완전한 내용을 배포하기 전에 저장해놓을 수 있어서 편리하다.

편집과정에서 cheat sheet를 찾아보면서 markdown을 작성할 수 있다. 이 부분이 아직 markdown이 익숙치 않은 나에게 매우 편리하게 느껴졌다.


````
Headers
---------------------------

# Header 1

## Header 2

### Header 3



Styling
---------------------------

*Emphasize* _emphasize_

**Strong** __strong__

==Marked text.==

~~Mistaken text.~~

> Quoted text.

H~2~O is a liquid.

2^10^ is 1024.



Lists
---------------------------

- Item
  * Item
    + Item

1. Item 1
2. Item 2
3. Item 3

- [ ] Incomplete item
- [x] Complete item



Links
---------------------------

A [link](http://example.com).

An image: ![Alt](img.jpg)

A sized image: ![Alt](img.jpg =60x50)



Code
---------------------------

Some `inline code`.

```
// A code block
var foo = 'bar';
```

```javascript
// An highlighted block
var foo = 'bar';
```



Tables
---------------------------

Item     | Value
-------- | -----
Computer | $1600
Phone    | $12
Pipe     | $1


| Column 1 | Column 2      |
|:--------:| -------------:|
| centered | right-aligned |



Definition lists
---------------------------

Markdown
:  Text-to-HTML conversion tool

Authors
:  John
:  Luke



Footnotes
---------------------------

Some text with a footnote.[^1]

[^1]: The footnote.



Abbreviations
---------------------------

Markdown converts text to HTML.

*[HTML]: HyperText Markup Language



LaTeX math
---------------------------

The Gamma function satisfying $\Gamma(n) = (n-1)!\quad\forall
n\in\mathbb N$ is via the Euler integral

$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$

````

> stack edit에서 제공하는 cheat sheet
