---
layout  : wiki
title   : neo vim swap 파일 에러 생길 때 
summary : 
date    : 2021-10-13 10:51:03 +0900
updated : 2021-10-14 14:37:33 +0900
tag     : neovim
toc     : true
public  : true
parent  : [[vim/index]]
latex   : false
---
* TOC
{:toc}

## neo vim swap file error 생길 때
모종의 이유로 에디터가 비정상 종료되어, 임시 파일이 삭제 되지 않고 남아있을 때 나타나는 현상.
임시 파일을 강제로 삭제 해주면 해결됨
- **~/.local/share/nvim/swap** 폴더 아래의 모든 파일을 삭제
- **rm -rf ~/.local/share/nvim/swap/***

