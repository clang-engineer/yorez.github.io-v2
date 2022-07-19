---
layout  : wiki
title   : autojump 
summary : 위치 이동을 편리하게 해주는 autojump
date    : 2022-07-19 09:10:09 +0900
updated : 2022-07-19 13:58:24 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# Autojump

## github
[https://github.com/wting/autojump](https://github.com/wting/autojump)

## 설치
### MacOS
```sh
$ brew install autojump
```

### Debian/Ubunto
```sh
$ sudo apt install autojump
```

### CentOS
```sh
$ yum install autojump
```

## sh 설정
### zshell 사용시 zshrc에 plugin 사용 설정 추가
```sh
plugins=(git autojump)
```

### bash shell 사용시
```sh
$ source /usr/share/autojump/autojump.sh on startup

// 상시 사용 원할 시
$ echo '. /usr/share/autojump/autojump.sh' >> ~/.bashrc
```

## 사용법
- help
```sh
$ j --help
```

- foo 키워드를 포함하는 디렉터리로 점프
```sh
$ j foo
```

- 현재 디렉터리의 자식 디렉터리로 점프
```sh
$ jc bar
```

- 위치의 파일 탐색기 열기 
```sh
$ jo music
```

- 다중 경로 지정
```sh
30  /home/user/mail/inbox
10  /home/user/work/index

$ j w in  # /home/user/work/index 로 이동
```

- jump 가중치 확인
```sh
$ j -s
```

- 존재하지 않는 경로 삭제
```sh
$ j --purge
```

> https://www.linode.com/docs/guides/faster-file-navigation-with-autojump/
