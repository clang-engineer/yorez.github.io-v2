---
layout  : wiki
title   : Mybatis 복수 db 이용
summary : 
date    : 2021-11-21 21:18:16 +0900
updated : 2021-11-21 21:52:29 +0900
tags    : 
toc     : true
public  : true
parent  : [[spring/index]]
latex   : false
---
* TOC
{:toc}


# 스프링 mybatis 사용시 두개 db 이용하기

## yaml 설정
```yaml
spring:
  datasource:
    hikari:
      primary:
        driver-class-name: org.h2.Driver
        jdbc-url: jdbc:h2:file:./build/h2db/db/healthcare_tableau;DB_CLOSE_DELAY=-1
        username: Healthcare_Tableau
        password:
      secondary:
        driver-class-name: org.h2.Driver
        jdbc-url: jdbc:h2:file:./build/h2db/db/healthcare_tableau;DB_CLOSE_DELAY=-1
        username: Healthcare_Tableau
        password:
```


## DB 설정1
```java
@Configuration
@EnableTransactionManagement
@MapperScan(value = {"com.test.dao.primary"}, sqlSessionFactoryRef = "primarySqlSessionFactory")
public class PrimaryDatasourceConfiguration {
    @Bean
    @Primary
    @Qualifier("primaryHikariConfig")
    @ConfigurationProperties(prefix = "spring.datasource.hikari.primary")
    public HikariConfig primaryHikariConfig() {
        return new HikariConfig();
    }

    @Bean
    @Primary
    @Qualifier("primaryDataSource")
    public DataSource primaryDataSource() {
        return new HikariDataSource(primaryHikariConfig());
    }

    @Primary
    @Bean(name = "primarySqlSessionFactory")
    public SqlSessionFactory sqlSessionFactory(@Qualifier("primaryDataSource") DataSource dataSource, ApplicationContext applicationContext) throws Exception {
        SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
        sqlSessionFactoryBean.setDataSource(dataSource);
        sqlSessionFactoryBean.setMapperLocations(applicationContext.getResources("classpath:mapper/primary/*.xml"));
        sqlSessionFactoryBean.setTypeAliasesPackage("com.test.service.dto");

        return sqlSessionFactoryBean.getObject();
    }

    @Primary
    @Bean(name = "primarySqlSessionTemplate")
    public SqlSessionTemplate sqlSessionTemplate(@Qualifier("primarySqlSessionFactory") SqlSessionFactory sqlSessionFactory) {
        return new SqlSessionTemplate(sqlSessionFactory);
    }
}
```

## DB 설정2
```java
@Configuration
@EnableTransactionManagement
@MapperScan(value = {"com.test.dao.secondary"}, sqlSessionFactoryRef = "secondarySqlSessionFactory")
public class SecondaryDatasourceConfiguration {
    @Bean
    @Qualifier("secondaryHikariConfig")
    @ConfigurationProperties(prefix = "spring.datasource.hikari.secondary")
    public HikariConfig secondaryHikariConfig() {
        return new HikariConfig();
    }

    @Bean
    @Qualifier("secondaryDataSource")
    public DataSource secondaryDataSource() {
        return new HikariDataSource(secondaryHikariConfig());
    }

    @Bean(name = "secondarySqlSessionFactory")
    public SqlSessionFactory sqlSessionFactory(@Qualifier("secondaryDataSource") DataSource dataSource, ApplicationContext applicationContext) throws Exception {
        SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
        sqlSessionFactoryBean.setDataSource(dataSource);
        sqlSessionFactoryBean.setMapperLocations(applicationContext.getResources("classpath:mapper/secondary/*.xml"));
        sqlSessionFactoryBean.setTypeAliasesPackage("com.test.service.dto");

        return sqlSessionFactoryBean.getObject();
    }

    @Bean(name = "secondarySqlSessionTemplate")
    public SqlSessionTemplate sqlSessionTemplate(@Qualifier("secondarySqlSessionFactory") SqlSessionFactory sqlSessionFactory) {
        return new SqlSessionTemplate(sqlSessionFactory);
    }
}
```
