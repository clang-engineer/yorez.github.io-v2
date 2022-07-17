---
layout  : wiki
title   : neovim 초기 셋팅하기
summary : 
date    : 2022-07-13 15:03:23 +0900
updated : 2022-07-17 23:15:55 +0900
tags    : 
toc     : true
public  : true
parent  : [[vim/index]]
latex   : false
---
* TOC
{:toc}

## neovim 설치

```sh
brew install neovim
```

## vim-plug 설치

```sh
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```

### nvim 설정 파일 최상단에 아래 내용 기입

```sh
call plug #begin('~/.vim/plugged')

Plug 'preservim/nerdtree' #plugin list

...

call plug #end()

set number # custom plugin list
...
```

## nvim 설정 파일

```sh
mkdir ~/.config/nvim
touch ~/.config/nvim/init.vim
```

## vim-plug로 plugin list 설치

- nvim 을 열고 :PlugInstall
