---
layout  : wiki
title   : CoC (Conquer of Completion)
summary : 
date    : 2022-07-13 16:15:41 +0900
updated : 2022-07-13 16:29:01 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 사용 동기

vim으로 IDE의 자동완성 기능을 사용하고 싶어 여러 유명 플러그인을 붙여보았지마 만족스러운 결과를 계속 얻지 못 했다.
그러다 vim -> neovim 으로 변경하면서 coc를 사용하게 되었고 제일 만족하며 사용할 수 있었다.

설치 순서는 저장소 [https://github.com/neoclide/coc.nvim](https://github.com/neoclide/coc.nvim) 에 잘 나와있다.

1. nodejs >= 12.12 설치
```sh
curl -sL install-node.vercel.app/lts | bash
```

2. vim-plug 에 추가
```sh
Plug 'neoclide/coc.nvim', {'branch': 'release'}
```

3. 설치
```sh
:PlugInstall 
```

4. CoC 언어별 플러그인 설치
```sh
:CocInstall coc-json coc-tsserver
```

```sh
# 아래 명령어 안 되면 >> :CocCommand clangd.install
:CocCommand coc-clangd
```


기타 추가 설정법은 위의 저장소 README를 참조
