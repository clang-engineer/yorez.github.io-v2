---
layout  : wiki
title   : 맥에서 마크다운 파일을 PDF로 변환하기
summary : 
date    : 2022-06-22 15:21:45 +0900
updated : 2022-06-22 15:34:04 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

## Convert markdown to pdf

### 시도1. markdown-pdf 사용  
```
npm install -g markdown-pdf
markdown-pdf /path/to/markdown
```
- 위 방법은 잘 되지만 이미지가 빠지는 에로 사항이 있었다.


### 시도2. pandoc 사용

```sh
brew install pandoc
brew cask install basictex
ln -s /Library/TeX/Distributions/.DefaultTeX/Contents/Programs/x86_64/pdflatex /usr/local/bin
pandoc *.md -o docs.pdf
```

- 아래의 내용을 참조해서 위 절차대로 진행했지만, 이미지 빠지는 문제와 라텍스 한글 인코딩 문제가 발생했다..
- [참조](https://eshlox.net/2019/12/09/use-pandoc-on-macos-to-convert-multiple-markdown-files-to-a-single-pdf-file)

### 시도3. grip 사용
```
pip install grip  
grip your_markdown.md
```

1. grip 을 설치
2. md 파일을 서버에서 활성화
3. 크롬으로 인쇄 -> pdf 옵선 사용

- 이 방법이 내가 선택한 제일 나은 방법 이었다..
- 주변에 Bear 라는 에디터를 사용해서 손쉽게 변환하신 분이 있었다. (다만, pdf 변환 기능은 유료 라이선스였다..)
