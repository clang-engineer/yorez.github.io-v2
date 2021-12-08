---
layout  : wiki
title   : http -> https로 보내기, 복수 포트 점령하기
summary : 
date    : 2021-11-11 08:30:41 +0900
updated : 2021-12-08 10:23:00 +0900
tags    : 
toc     : true
public  : true
parent  : [[java/index]]
latex   : false
---
* TOC
{:toc}

 
## undewtow 복수 포트 점령하기

### http -> https로

```java
@Configuration
public class UndertowConfig {

    @Value("${http.port:0}")
    private int httpPort;

    @Value("${server.port:0}")
    private int sslPort;

    @Bean
    @Profile(JHipsterConstants.SPRING_PROFILE_PRODUCTION)
    public ServletWebServerFactory serverFactory() {
        UndertowServletWebServerFactory factory = new UndertowServletWebServerFactory();

        factory.addBuilderCustomizers(builder -> {
            builder.addHttpListener(httpPort, "0.0.0.0");
        });

        factory.addDeploymentInfoCustomizers(deploymentInfo -> {
            deploymentInfo.addSecurityConstraint(
                new SecurityConstraint()
                    .addWebResourceCollection(new WebResourceCollection().addUrlPattern("/*"))
                    .setTransportGuaranteeType(TransportGuaranteeType.CONFIDENTIAL)
                    .setEmptyRoleSemantic(SecurityInfo.EmptyRoleSemantic.PERMIT))
                .setConfidentialPortManager(exchange -> sslPort);
        });

        return factory;
    }
}
```

