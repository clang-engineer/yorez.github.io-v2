---
layout  : wiki
title   : jenkins
summary : 
date    : 2021-10-19 15:23:23 +0900
updated : 2021-11-21 22:04:50 +0900
tags    : 
toc     : true
public  : true
parent  : [[etc/index]]
latex   : false
---
* TOC
{:toc}

## window
###start.bat

```
@echo
java -Dserver.port=8080 -jar C:\~~\test.jar
```

###stop.bat
```
@ECHO OFF
SET killport=8080
for /f "tokens=5" %%p in ('netstat -aon ^| find /i "listening" ^| find "%killport%"') do taskkill /F /PID %%p
```

###restart.bat
@echo off
START /B CMD /C CALL "C:\~~\stop.bat" [args [...]] >NUL 2>&1
START javaw -Dserver.port=8080 -jar C:\~~\test.jar
exit


### jenkins script
copy build\libs\test.jar C:\~~\
# jenkins sample
![Screen Shot 2021-10-19 at 2 02 53 PM](https://user-images.githubusercontent.com/39648594/137854726-0df551e0-2773-4193-b571-5527c008948d.png)

