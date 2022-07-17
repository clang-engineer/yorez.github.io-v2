---
layout  : wiki
title   : Vim 옵션정리 
summary : 
date    : 2022-07-16 05:13:44 +0900
updated : 2022-07-17 13:30:21 +0900
tags    : 
toc     : true
public  : true
parent  : [[vim/index]]
latex   : false
---
* TOC
{:toc}

# vim 옵션 정리

| 옵션                                  | 기능                                                 |
|---------------------------------------|------------------------------------------------------|
| set nocompatible                      | 오리지널 vi와호환되지 않음                           |
| set autoindent                        | 자동 듷여쓰기                                        |
| set cindent                           | C 프로그래밍용 자동들여쓰기                          |
| set smartindent                       | 스마트한 들여쓰기                                    |
| set wrap                              |                                                      |
| set nowrapscan                        | 검색할 떄 문서의 끝에서 처음으로 돌아감              |
| set nobackup                          | 백업파일을 안만듬                                    |
| set visualbell                        | 키를 잘못눌렀을 때 화면 표시                         |
| set ruler                             | 화면 우측 하단에 현재 커서의 위치(줄, 칸) 표시       |
| set shilftwidth=4                     | 자동 들여쓰기 4칸                                    |
| set number                            | 행번호 표시, set nu가능                              |
| set fencs=ucs-bom,utf-8,euc-kr,latin1 | 한글 파일은 euc-kr로, 유니코드는 유니코드로          |
| set fileencoding=utf-8                | 파일 저장 인코딩                                     |
| set tenc=utf-8                        | 터미널 인코딩                                        |
| set expandtab                         | 탭 대신 스페이스                                     |
| set hlsearch                          | 검색어 강조, set his도 가능                          |
| set ignorecase                        | 검색 시 대소문자 무시, set ic도 가능                 |
| set tabstop=4                         | 탭을 4칸으로                                         |
| set lbr                               |                                                      |
| set incsearch                         | 키워드 입력시 점진적 검색                            |
| syntax on                             | 구문강조 사용                                        |
| filetype indent on                    | 파일 종류에 따른 구문강조                            |
| set background=dark                   | 하이라이팅 light / dark                              |
| colorscheme desert                    | vi 색상 테마 설정                                    |
| set backspace=eol,start,indent        | 줄을 끝, 시작, 들여쓰기에서 백스페이스시 이전종료    |
| set history=1000                      | vi 편집기록 기억갯수 .viminfo에 기록                 |
