---
layout  : wiki
title   : plugin 정리
summary : 
date    : 2021-10-01 08:22:16 +0900
updated : 2021-12-08 18:00:10 +0900
tags    : vim plugin
toc     : true
public  : true
parent  : [[vim/index]]
latex   : false
---
* TOC
{:toc}

# [Vim Awesome](https://vimawesome.com/) 을 참조해서 유용한 플러그인 정리

## Language
### The NERD Commenter
- 주석을 편리하게 돕는 플러그인
 
```
- [count]<leader>cc |NERDCommenterComment|
- [count]<leader>cn |NERDCommenterNested|
- [count]<leader>c<space> |NERDCommenterToggle|
- [count]<leader>cm |NERDCommenterMinimal|
- [count]<leader>ci |NERDCommenterInvert|
- [count]<leader>cs |NERDCommenterSexy|
- [count]<leader>cy |NERDCommenterYank|
- <leader>c$ |NERDCommenterToEOL|
- <leader>cA |NERDCommenterAppend|
- <leader>ca |NERDCommenterAltDelims|
- [count]<leader>cl |NERDCommenterAlignLeft [count]<leader>cb |NERDCommenterAlignBoth
- [count]<leader>cu |NERDCommenterUncomment|
```

### Emmmet.vim
- vim용 emmet플러그인

### ale
- 문법 체크해주고 교정해주는 플러그인

## Completion
### youcompleteme
- 코드 자동완성 플러그인
 
### vim snippets
- 자주 사용하는 구문을 등록해놓을 수 있는 플러그인

### vim endwise
- 종료 태그를 자동생성

### delimitmate
- 따옴표, 괄호, 중괄호 등을 자동으로 닫아줌

### taglist

### auto pairs
- 짝으로 따옴표, 괄호, 중괄호 삽입, 삽제

### close tag
- html 태그 닫기

### vim gutentags
- vim으로 코드를 편집하는 동안 백그라운드에서 자동으로 tags 파일을 갱신

## Code display
### Surround vim
- 특정 영역을 원하는 문자로 감쌈.
- cs: 변경
- ys: 추가
- ds: 삭제

```
"Hello world!" // 이 문자열을 대상으로 테스트

//cs"'
'Hello world!'

//cs'<q>
<q>Hello world!</q>

//cst"
"Hello world!"

//ds"
Hello world!

//ysiw]
[Hello] world!

//cs]{
{ Hello } world!

//yssb or yss).
({ Hello } world!)

ds{ds)
Hello world!

//ysiw<em>
<em>Hello</em> world!

//<V> + S + <p class="important">.
<p class="important">
  <em>Hello</em> world!
</p>
```


## Integration

## Interface

## Commands

## Other
