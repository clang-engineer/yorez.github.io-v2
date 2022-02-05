---
layout  : wiki
title   : 맥북 셋팅
summary : 
date    : 2022-02-05 16:24:30 +0900
updated : 2022-02-05 16:48:43 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

## old 맥북에서 new 맥북으로 이사가기

### Brewfile 생성
```sh
brew install mac
brew bundle dump
```
- brew bundle dump의 결과 Brewfile이 생성됨 누락된 어플리케이션이 있다면 수동으로 설치
(brew cask를 활용하여 gui 기반의 어플리케이션을 관리한다면 Brewfile에 추가됨)

## new 맥북에서 할일

### Homebrew 설치
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### Brewfile 생성
old 맥북에서 생성한 Brewfile을 다운받고 다운받은 위치에서 brew bundle 실행
```sh
brew bundle
```

### sshkey 생성
```sh
ssh-keygen
```
생성된 공개키를 github settings - SSH and GPG keys - SSH keys에 등록

~/.ssh/config 파일을 생성하고 다음과 값이 추가
```sh
# personl account-yorez 
host github.com-yorez
hostname github.com
user git
    identityfile ~/.ssh/id_rsa_yorez
# business account-planit-zero
host github.com-planit-zero
hostname github.com
user git
    identityfile ~/.ssh/id_rsa_planit-zero
```

연결 확인
```sh
ssh -T github.com-yorez
ssh -T github.com-planit-zero
```

### vim 설정

### Jebrains Toolbox 다운로드


###
