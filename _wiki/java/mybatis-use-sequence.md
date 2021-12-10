---
layout  : wiki
title   : mybatis 데이터 삽입시 시퀀스 다음값 얻기
summary : 
date    : 2021-11-22 09:53:55 +0900
updated : 2021-12-10 09:56:31 +0900
tags    : 
toc     : true
public  : true
parent  : [[java/index]]
latex   : false
---
* TOC
{:toc}

## 예시
```xml
<mapper namespace="io.test.TestDao">
    <insert id="save">
        <selectKey keyProperty="IDENTIFIER_SEQUENCE" resultType="java.lang.Integer" order="BEFORE">
            select SEQUENCE_GENERATOR.NEXTVAL from dual
        </selectKey>
        INSERT INTO tbl_test (id, title, description)
        VALUES (#{IDENTIFIER_SEQUENCE}, 'title', 'desciption')
    </insert>
</mapper>
```

## select SEQUENCE_GENERATOR.NEXTVAL from dual
- SEQUENCE_GENERATOR의 다음 시퀀스를 가져오기 위함. DUAL은 임시 테이블.
- 현재 시퀀스를 가져오고 싶다면 CURRVAL을 사용.

## keyProperty
- keyProperty는 SELECT SEQUENCE_GENERATOR.NEXTVAL FROM DUAL의 값을 받는 변수. 
 
## order
- 시퀀스를 생성하는 시기를 결정.
- before, after 각각 쿼리문 실행 전, 후에 시퀀스 값 생성.

## resultType
- 반환값의 데이터형

* <insert> 가 사용하는 parameterType 에 sequnse keyProperty 를 setting 할 수 있는 속성과 setter 메서드가 있어야 한다!

