---
layout  : wiki
title   : mybatis key-value map 객체 동적으로 사용하기
summary : 
date    : 2021-11-21 21:45:32 +0900
updated : 2021-11-21 21:52:11 +0900
tags    : 
toc     : true
public  : true
parent  : [[spring/index]]
latex   : false
---
* TOC
{:toc}

# mybatis key-value map 동적으로 사용하기

## xml excample
**#{row.${column}}** 처럼 사용하면 row(map객체)의 column(key)에 해당하는 값(value)을 동적으로 읽어들일 수 있다.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.test.dao.ExcelDao">
    <insert id="save">
        INSERT INTO ${tableName}
        <foreach item="column" collection="header" open="(" separator="," close=")">
            ${column}
        </foreach>
        VALUES
        <foreach item="column" collection="header" open="(" separator="," close=")">
            #{row.${column}}
        </foreach>
    </insert>
</mapper>

```
