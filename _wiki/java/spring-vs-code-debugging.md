---
layout  : wiki
title   : vs code로 스프링 디버깅을 원할 경우
summary : 
date    : 2021-12-23 10:57:57 +0900
updated : 2021-12-24 16:40:39 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 필요 확장팩

Extension pack for Java
Spring Boot Extension Pack
Gradle Extension Pack 
Lombok Annotation Support for VS Code
Vim

## Java Debugging 위한 셋팅

### setting.json

```
"java.home": "/Library/Java/JavaVirtualMachines/jdk-11.0.5.jdk/Contents/Home",
"gradle.javaDebug": {
    "tasks": [
        "bootRun"
    ],
    "clean": true
}
```

### main함수가서 run or debug
- launch.json 생성됨
 
### launch.json
```
"version": "0.2.0",
"configurations": [
    {
        "type": "java",
        "name": "Launch TestSystemApp",
        "request": "launch",
        "mainClass": "com.zero.TestSystemApp",
        "projectName": "testsystem",
        "vmArgs": [
            "-Dspring.profiles.active=dev",
            "-Djasypt.encryptor.password=1234"
        ],
        "console": "internalConsole"
    }, 
]
```

