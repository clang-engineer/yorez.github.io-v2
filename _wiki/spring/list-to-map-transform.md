---
layout  : wiki
title   : collection list to map 변환
summary : 
date    : 2021-12-05 12:01:53 +0900
updated : 2021-12-05 12:22:33 +0900
tags    : 
toc     : true
public  : true
parent  : [[spring/index]]
latex   : false
---
* TOC
{:toc}


## 객체 list를 map으로 변환하기

- title, deription을 속성으로 가지고 있는 test domain의 list을 Map<key,value> 형태로 변환
 
```java
public class ListToMapTransform{
    public static void main(String[] args){
        Map<String, String> result = testRepository.findAll()
            .stream()
            .filter(test -> StringUtils.isNotEmpty(test.getTitle()) && StringUtils.isNotEmpty(test.getDescription()))
            .collect(Collectors.toMap(i1 -> i1.getTitle(), i2 -> i2.getDescription()));
    }
}
```

