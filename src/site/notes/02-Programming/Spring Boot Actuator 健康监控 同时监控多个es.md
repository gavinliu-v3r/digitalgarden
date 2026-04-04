---
{"aliases":null,"created":"Thursday, April 2nd 2026, 7:18:29 pm","modified":"Saturday, April 4th 2026, 3:52:24 pm","dg-publish":true,"tags":["Develop/Java","1-Areas"],"related":["[[Spring Boot Actuator]]"],"author":"Gavin","permalink":"/02-Programming/Spring Boot Actuator 健康监控 同时监控多个es/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Thursday, April 2nd 2026, 7:18:29 pm","modified":"Saturday, April 4th 2026, 3:52:24 pm","tags":["Develop/Java","1-Areas"],"related":["[[Spring Boot Actuator]]"],"author":"Gavin"}}
---


## Spring Boot Actuator 健康监控 同时监控多个 es

**actuator 健康监控 多个 es**

```java
package com.jdcloud.microservice.customer.engine.common.configuration.es;

import lombok.extern.slf4j.Slf4j;
import org.elasticsearch.action.search.SearchRequest;
import org.elasticsearch.action.search.SearchResponse;
import org.elasticsearch.client.RequestOptions;
import org.elasticsearch.client.RestHighLevelClient;
import org.springframework.boot.actuate.health.Health;
import org.springframework.boot.actuate.health.HealthIndicator;
import org.springframework.http.HttpStatus;
import org.springframework.stereotype.Component;

import javax.annotation.Resource;
import java.io.IOException;

/**
 * actuator健康监控 多个es
 *
 * @author liuzekun
 * Create at 2023/7/4
 */
@Component
@Slf4j
public class ElasticsearchHealthIndicator implements HealthIndicator {

    @Resource(name = "userInfoElasticsearchClient")
    private RestHighLevelClient userInfoRestHighLevelClient;
    @Resource(name = "operateLogElasticsearchClient")
    private RestHighLevelClient operateLogRestHighLevelClient;

    /**
     * 健康检测
     * @param
     * @return org.springframework.boot.actuate.health.Health
     */
    @Override
    public Health health() {
        try {
            boolean userInfoElasticsearchHealthy = isElasticsearchHealthy(userInfoRestHighLevelClient);
            boolean operateLogElasticsearchHealthy = isElasticsearchHealthy(operateLogRestHighLevelClient);
            log.info("ElasticsearchHealthIndicator isElasticsearchHealthy userInfoElasticsearchHealthy:{},operateLogElasticsearchHealthy:{}", userInfoElasticsearchHealthy, operateLogElasticsearchHealthy);
            if (userInfoElasticsearchHealthy && operateLogElasticsearchHealthy) {
                return Health.up().build();
            } else {
                return Health.down().build();
            }
        } catch (Exception e) {
            return Health.down(e).build();
        }
    }

    /**
     * 检查Elasticsearch客户端是否健康的逻辑
     *
     * @param client
     * @return boolean
     */
    private boolean isElasticsearchHealthy(RestHighLevelClient client) {
        try {
            SearchRequest searchRequest = new SearchRequest();
            SearchResponse searchResponse = client.search(searchRequest, RequestOptions.DEFAULT);
            int statusCode = searchResponse.status().getStatus();
            return statusCode == HttpStatus.OK.value();
        } catch (IOException e) {
            return false;
        }
    }
}
```
