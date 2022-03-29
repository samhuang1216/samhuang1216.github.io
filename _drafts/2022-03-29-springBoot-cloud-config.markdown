---
layout: post
title:  "spring boot cloud config順序及相關"
date:   2022-03-29
categories: spring
tags: [spring, cloud]
---

## spring boot project load config from config server/consul kv

### spring.cloud.config server -client-bootstrap.yml

``` yaml
spring:
  application:
    name: stock
  profiles:
    active: dev
    config:
      uri: http://localhost:7000
      fail-fast: true
```

### spring.cloud.config server -client-pom

``` xml
  <dependency>
   <groupId>org.springframework.cloud</groupId>
   <artifactId>spring-cloud-starter-config</artifactId>
  </dependency>
  <dependency>
   <groupId>org.springframework.cloud</groupId>
   <artifactId>spring-cloud-starter-bootstrap</artifactId>
  </dependency>
```

### filename

設定properties檔後啟動專案，可[透過下面url格式](https://cloud.spring.io/spring-cloud-config/reference/html/#_locating_remote_configuration_resources)取得對應的設定檔資源。

```shell
/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties
```

### config server setting

#### application.yml

```yaml
server:
 port: 7000
spring:
  profiles:
    active: native
  cloud:
    config:
      server:
        native:
          searchLocations: classpath:/service/conf

  application:
    name: server-config
```

#### main class

``` java
@EnableConfigServer
```

### consul config-client POM

``` xml
<dependency>
   <groupId>org.springframework.cloud</groupId>
   <artifactId>spring-cloud-starter-consul-config</artifactId>
  </dependency>
```

### consul config -client bootstrap.yml

``` yaml
spring:
  application:
    name: serviceStock
  profiles:
    active: dev
  cloud:
    consul:
      host: 127.0.0.1
      port: 8500
      discovery:
        prefer-ip-address: true
        health-check-path: /actuator/health
      config:
        enabled: true
        format: YAML
        prefixes: config 
        defaultContext: ${spring.application.name}
        profileSeparator: ','
        data-key: data
```

### consul KV-create

key值為上述設定
${prefixes}/${defaultContext}${profileSeparator}${spring.profiles.active}/${data-key}

指定檔案格式，貼上相關設定，即可。
