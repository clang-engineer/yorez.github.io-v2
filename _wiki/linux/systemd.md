---
layout  : wiki
title   : 리눅스 서비스 관리 데몬 systemd 
summary : 
date    : 2022-05-06 13:59:50 +0900
updated : 2022-05-06 14:17:02 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}


## 커스텀 서비스 등록
/usr/lib/systemd/[servicename].service 파일 생성

```sh
[Unit]
Description=Register Service [servicename]

[Service]
User=root
Group=root
Environment="PATH=/bin:/usr/local/sbin/:/usr/local/bin:/usr/sbin:/usr/bin:/usr/local/node/bin"
WorkingDirectory=/home/test
ExecStart=/home/test/start.sh

[Install]
WantedBy=multi-user.target
```

### /usr/lib/systemd/system vs /etc/systemd/syste
- /usr/lib/systemd/system
OS 벤더사가 관리하는 영역으로 배포 저장소(Distribution repository)에서 다운로드되는 패키지로 제공되는 파일들이 위치한다.

- /etc/systemd/system
시스템 관리자가 관리하는 영역으로 시스템 특정(System-specific)한 유닛들이 위치한다.

벤더사에서 제공하는 유닛들중 자신의 시스템에 맞게 수정하고 싶은 내용이 있을 경우 /etc/ssystemd/system에 유닛을 추가하면 해당 유닛을 오버라이드하게 된다. (/etc/ssystemd/system에 없는 유닛들은 벤더사에서 제공하는 기본 유닛을 사용한다.)

> https://unix.stackexchange.com/questions/206315/whats-the-difference-between-usr-lib-systemd-system-and-etc-systemd-system


## systemctl enable [servicename]
## systemctl start [servicename]
## systmectl status [servicename]
## systmectl stop [servicename]
## systmectl disable [servicename]
## systmectl daemon-reload
## systmectl reset-failed

## 서비스 삭제 절차
```sh
//step by step
systemctl stop [servicename]
systemctl disable [servicename]
rm /etc/systemd/system/[servicename]
rm /etc/systemd/system/[servicename] # and symlinks that might be related
rm /usr/lib/systemd/system/[servicename] 
rm /usr/lib/systemd/system/[servicename] # and symlinks that might be related
systemctl daemon-reload
systemctl reset-failed
```

```sh
// oneline
service=YOUR_SERVICE_NAME; systemctl stop $service && systemctl disable $service && rm /etc/systemd/system/$service &&  systemctl daemon-reload && systemctl reset-failed
```

