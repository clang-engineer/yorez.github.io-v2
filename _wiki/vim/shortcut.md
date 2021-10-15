---
layout  : wiki
title   : 유용한 vim shortcut 정리 
summary : 
date    : 2021-10-06 13:44:14 +0900
updated : 2021-10-15 11:23:41 +0900
tags    : 
toc     : true
public  : private
parent  : 
latex   : false
---
* TOC
{:toc}

## 문단 모양

### >%, >ib, >at
- 중소괄호 구간, 소괄호 내부, 태그 구간 들여쓰기

--- 
## 여러 파일 편집

### \<C-w> + x
- 창 바꾸기

### \<C-w> + _
- 가로 분리일 때 zoom in

### \<C-w> + | 
- 세로 분리일 때 zoom in

### \<C-w> + =
- 창 크기 동일하게 조정


---
## 자동완성

### \<C-p> \<C-n>
- vim 기본 자동완성 insert 모드에서 ctrl + p, ctrl + n을 누르면
vim의 complete 옵션에서 지정한 키워드를 기반으로 자동완성해줌

### \<C-x>
- insert 모드에서만 지원하는 자동완성
- \<C-x>\<C-l>: 라인단위 자동완성
- \<C-x>\<C-f>: 파일명, 경로 자동완성

### abbreviate
- 축약어를 등록할 수 있다. 오타교정, 자동완성등의 용도로 유용하게 사용할 수 있다. 
 
1. abbr: insert, command 모드 모두 작동
2. iabbr: insert 모드에서만 작동
3. cabbr: command 모드에서만 작동

```vim
//.vimrc 파일에 다음과 같이 등록해놓고 사용할 수 있다.
//오타교정
abbr consolee console
abbr coment comment

//자동완성
abbr cns console.log()
abbr cmt /* */

//<Esc>를 활용해 normal 모드 복구
abbr cmt /* */<Esc>hhi

//기타 
//<expr>을 사용하면 스크립트 실행 결과로 완성
iabbr __email abcd@efgh.com
iabbr <expr> __time strftime("%Y-%m-%d %H:%M:%S")
iabbr <expr> __file expand('%:p')
iabbr <expr> __name expand('%')
iabbr <expr> __pwd expand('%:p:h')
iabbr <expr> __branch system("git rev-parse --abbrev-ref HEAD")
```
> 참조: <https://johngrib.github.io/wiki/vim-auto-completion/>
