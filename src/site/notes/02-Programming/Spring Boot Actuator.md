---
{"aliases":null,"created":"Thursday, April 2nd 2026, 4:58:44 pm","modified":"Saturday, April 4th 2026, 3:52:06 pm","dg-publish":true,"tags":["Develop/Java","1-Areas"],"related":"","author":"Gavin","permalink":"/02-Programming/Spring Boot Actuator/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Thursday, April 2nd 2026, 4:58:44 pm","modified":"Saturday, April 4th 2026, 3:52:06 pm","tags":["Develop/Java","1-Areas"],"related":"","author":"Gavin"}}
---


**播客：**​[https://www.cnblogs.com/caoweixiong/p/15325382.html](https://www.cnblogs.com/caoweixiong/p/15325382.html)

**可以作为 k8s 探针接口（eg: 就绪探针，存活探针）**

```plain
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

 **/actuator/health**和 **/actuator/info**

```plain
curl -XGET 'http://localhost:9091/api/actuator/health'
```

```properties
management:
  server:
    port: 9091
  endpoints:
    web:
      exposure:
        # 打开所有的监控点
        include: health
      # api 前缀，避开filterChain
      base-path: /api/actuator
  endpoint:
    health:
      show-details: always
    shutdown:
      # 通过指定接口关闭 SpringBoot
      enabled: false
```
