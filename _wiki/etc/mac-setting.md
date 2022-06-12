---
layout  : wiki
title   : 맥북 셋팅
summary : 
date    : 2022-02-05 16:24:30 +0900
updated : 2022-06-12 03:31:21 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

> 출처: https://johngrib.github.io/wiki/migrate-to-new-macbook/

## 새 맥북 셋팅하기 

### Brewfile 생성
```sh
brew install mac
brew bundle dump
```
- brew bundle dump의 결과 Brewfile이 생성됨 누락된 어플리케이션이 있다면 수동으로 설치
(brew cask를 활용하여 gui 기반의 어플리케이션을 관리한다면 Brewfile에 추가됨)

## new 맥북에서 할일

### xcode-select 설치
```sh
xcode-selct --install
```

### Homebrew 설치
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### Brewfile 실행
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
- vim-plug를 설치한다

### Jebrains Toolbox 다운로드
- 라이선스를 갖고 있는 IDE를 추가로 설치

### tmux 설정

### zsh 설정
1. intall zsh
```sh
sudo apt-get update
sudo apt-get intall zsh -y
chsh -s /usr/bin/zsh # change default shell
```
2. install on my zsh
```sh
# Curl을 이용한 설치
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# wget을 이용한 설치
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
3. install zsh plugin
```sh
# zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

brew

# autojump
apt intall autojump
```

## 취향

### 세 손가락 드래그
- 시스템 환경설정 - 손쉬운 사용 - 포인트 제어기 - 트랙패드 옵션
    - 드래그 활성화에서 세 손가락으로 드래그하기
