---
layout  : wiki
title   : journalctl 사용법
summary : 
date    : 2022-05-13 13:30:44 +0900
updated : 2022-05-13 13:49:41 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]]
latex   : false
---
* TOC
{:toc}

# journalctl
- 리눅스용 시스템/서비스 매니저인 systemd 는 로그 데이타를 journal 이라는 바이너리 형식으로 저장함.
- systemd-journald.service에 의해서 systemd의 정보들을 분석.
- 옵션없이 journalctl 을 실행하면 systemd 의 로그를 출력함.

# 설정파일
- /etc/systemd/journald.conf

# 사용예시
## 최근 메시지만 보기

- -n 옵션을 사용하면 최근 10 개 메시지만 표시.

```bash
journalctl -n   // 기본 최근 10개 메시지 표시
journalctl -n 7 //최근 7개 메시지 표시
```

## message catalog 사용
- -x 옵션을 추가하면 message catalog 에서 해당 저널에 대한 상세 설명을 추가해서 출력.

```bash
journalctl -xn
```

## 마지막 라인 표시
- -n  옵션을 사용하지 않을 경우 처음 저널부터 표시합니다. -e(pager end) 옵션을 주면 pager 를 사용해서 마지막 에러 메시지 라인부터 출력.

```bash
journalctl -x -e
```

## 짤리는 페이지 개행하기

```bash
journalctl -xn --no-pager | less
```

## 변경 사항 계속 보기
- tail -f 옵션처럼 -f 를 사용하면 마지막 로그 내용을 보여준 후에 이후에 변경되는 로그 파일의 내용을 계속 출력.

```bash
journalctl -f
```

## 특정 PID 저널만 보기
- _PID={PID} 옵션을 사용하면 특정 PID 관련한 저널을 출력. 

```bash
journalctl -n _PID=872  //  pid 가 872 인 프로세스가 생성한 최근 10개의 저널 출력
```

## 우선 순위로 필터링하기

- -p 옵션을 사용하면 저널의 우선 순위(emerg, alert, crit, err, warning, notice, info, debug) 에 따라 저널을 필터링해서 출력.
```bash
journalctl -p critical 
```

## 날짜/시간으로 필터링
- --since 와 --until 옵션을 사용하면 특정 기간내의 저널만 출력.
```bash
journalctl --since 2020-01-09
journalctl --since 2020-01-09 --until 2020-01-11
journalctl --since yesterday --until tomorrow
journalctl --since "-2hour" --until "10min"
```

> 출처: https://www.lesstif.com/system-admin/linux-journalctl-82215080.html
