---
layout  : wiki
title   : 두개의 map 합치기
summary : 
date    : 2021-12-05 12:12:47 +0900
updated : 2021-12-08 10:22:29 +0900
tags    : 
toc     : true
public  : true
parent  : [[java/index]]
latex   : false
---
* TOC
{:toc}

## HashMap.putAll()

- 같은 key가 있을 때, value를 덮어 씀.

```java
import java.util.HashMap;
import java.util.Map;
public class MergeHashMap {
    public static void main(String[] args) {
        // Map 1 준비
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("Apple", 1000);
        map1.put("Banana", 2000);
        map1.put("Orange", 3000);
        
        // Map 2 준비
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("Apple", 4000);
        map2.put("Tomato", 5000);
        map2.put("WaterMelon", 6000);
        
        // Map1 + Map2
        map1.putAll(map2);
        
        // 결과 출력
        System.out.println(map1); // {Apple=4000, WaterMelon=6000, Tomato=5000, Orange=3000, Banana=2000}
    }
}
```

## HashMap.merge - Java8 이후

```java
import java.util.HashMap;
import java.util.Map;
public class MergeHashMap {
    public static void main(String[] args) {
        // Map 1 준비
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("Apple", 1000);
        map1.put("Banana", 2000);
        map1.put("Orange", 3000);
        
        // Map 2 준비
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("Apple", 4000);
        map2.put("Tomato", 5000);
        map2.put("WaterMelon", 6000);
        
        // Map1 + Map2
        map2.forEach((key, value) -> map1.merge(key, value, (v1, v2) -> v2));
        
        // 결과 출력
        System.out.println(map1); // {Apple=4000, WaterMelon=6000, Tomato=5000, Orange=3000, Banana=2000}
    }
}
```

## 같은 key일 경우, value합계 반영하기
```java
mport java.util.HashMap;
import java.util.Map;
public class MergeHashMap {
    public static void main(String[] args) {
        // Map 1 준비
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("Apple", 1000);
        map1.put("Banana", 2000);
        map1.put("Orange", 3000);
        
        // Map 2 준비
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("Apple", 4000);
        map2.put("Tomato", 5000);
        map2.put("WaterMelon", 6000);
        
        // Map1 + Map2
        map2.forEach((key, value) -> map1.merge(key, value, (v1, v2) -> v1 + v2));
        
        // 결과 출력
        System.out.println(map1); // {Apple=5000, WaterMelon=6000, Tomato=5000, Orange=3000, Banana=2000}
    }
}

출처: https://hianna.tistory.com/580 [어제 오늘 내일]

```
