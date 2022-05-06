---
layout  : wiki
title   : Offline 환경에서 커스텀 주피터 허브 환경 구축 하기
summary : 
date    : 2022-05-06 13:29:29 +0900
updated : 2022-05-06 13:56:04 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

# 기반 프로그램 설치
- python3, pip, node, npm
- pip -> nexus 설정
- node offline 설치


## node offline 설치
https://nodejs.org 에서 리눅스용 바이너리 패키지를 다운로드 받고 서버에 업로드
/etc/profile 에 환경변수 설정 추가

```sh
// /etc/profile
export NODE_HOME=/url/local/node
export PATH=$NODE_HOME/bin:$PATH
```

# nexus를 통한 의존성 설치
- npm --registry https://nexus.h-firework.com/repository/npm/ install -g configurable-http-proxy


# custom jupyterhub 셋팅
1. 소스코드 서버에 업로드
2. 파이썬 가상환경 생성: python3 -m venv ./venv
3. 패키지 의존성 설치: ./venv/bin/pip install -r ./dev-requirements.txt
4. 주피터 허브 설치: ./venv/bin/pip install jupyterhub
5. 주피터 랩, 노트북 설치: ./venv/bin/pip install jupyterlab notebook
6. 주피터를 pip 전역 모듈로 설치: python3 -m pip install --editable .
(6.이 안 될 경우 pip 패키지 저장소 (venv/lib/python3.9/site-packages)에 강제 업로드(cp -rf  jupyterhub ./venv/lib/python3.7/site-packages)하고 가상환경에서 실행)

# jupyterhub 시작 절차
- jupyterhub -f ./jupyterhub_config_custom.py
(가상환경 기반으로 시작할 경우 ./venv/bin/jupyterhub -f ./jupyterhub_config_custom.py)
