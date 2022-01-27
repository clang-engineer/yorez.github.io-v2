---
layout  : wiki
title   : 유용한 shell script 
summary : 
date    : 2021-10-13 12:57:35 +0900
updated : 2022-01-27 10:10:08 +0900
tags    : 
toc     : true
public  : true
parent  : [[linux/index]] 
latex   : false
---
* TOC
{:toc}

# 유용한 shell script

## java Jar 파일을 백그라운드로 실행
```shell
#!/bin/sh
nohup java -jar xxx.jar &
```

## port 번호로 프로세스 종료
```shell
#!/bin/sh
pid="$(lsof -t -i :$1 -s TCP:LISTEN)";

if [ "$pid" != "" ]; then
  kill -9 $pid;
  echo "$1 port num";
  echo "$pid process kill complete";
else
  echo "port num $1";
  echo "pid is empty";
fi
```
위 파일을 stop.sh 로 저장하고, **./stop.sh 80**와 같은 식으로 사용하면 
80포트를 사용하는 프로세스를 강제 종료시킨다


## 폴더 내 파일 명 일괄 변경 

```sh
for file in *_h.png
do
  mv "$file" "${file/_h.png/_half.png}"
done
```

- #!/bin/bash를 기입시 아래와 같이 한줄로 써야하므로 작성x
```sh
for file in *.png; do mv "$file" "${file/_h.png/_half.png}"; done
```
