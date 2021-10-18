---
layout  : wiki
title   : 한 컴퓨터에서 여러 개의 깃허브 계정 사용하기
summary : 
date    : 2021-10-18 10:08:34 +0900
updated : 2021-10-18 10:58:27 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

## ssh-key 생성
### 명령어
```bash
//각 이메일 주소는 깃허브 로그인 계정
$> ssh-keygen -t rsa -C "your_personal_email@domain.com" -f "id_rsa_personal"
$> ssh-keygen -t rsa -C "your_work_email@domain.com" -f "id_rsa_work"
```

### ~/.ssh 디렉터리에 공개키과 사설키가 생성됨
```
id_rsa_personal
id_rsa_personal.pub
id_rsa_work
id_rsa_work.pub
```

## ssh-key 등록 및 설정
### 생성한 키를 로컬 pc에 등록
```
$> ssh-add id_rsa_personal
$> ssh-add id_rsa_work
```

### 등록 확인
```
ssh-add -l
```

### ~/.ssh/config 수정 (없으면 직접 생성)
```
# Personal account-personal config 
Host github.com-personal
HostName github.com
User git
    IdentityFile ~/.ssh/id_rsa_personal
# Personal account-work config
Host github.com-work
HostName github.com
User git
    IdentityFile ~/.ssh/id_rsa_work
```

### 설정 확인
```
$> ssh -T github.com-personl
 # Hi PERSONAL! You've successfully authenticated, but GitHub does not provide shell access.
$> ssh -T github.com-work
 # Hi WORK! You've successfully authenticated, but GitHub does   not provide shell access.
```


## git 설정
### github에 공개키를 등록
~/.ssh/ 안에 id_rsa_userA.pub 와 id_rsa_userB.pub 내용 각각 복사\\
**github >> settings >> SSH and GPG keys**에서 각각의 공개키를 등록

### 각 로컬 저장소의 .git/config에 사용할 사용자 email 등록
```
// ~/work/workA
[user]
    email = your_work_email@domain.com
    
// ~/personal/projectA
[user]
    email = your_personal_email@domain.com
```

### 저장소 remote url 설정
```		
git remote set-url origin git@github.com-work:work/projectA.git
```


> 참조: \\
https://medium.com/the-andela-way/a-practical-guide-to-managing-multiple-github-accounts-8e7970c8fd46 \\
https://velog.io/@jay/multiplegithubaccounts
