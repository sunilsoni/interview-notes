---
layout: default
title: Spring Cloud
parent: Spring
resource: true
desc: "Spring Cloud interview questions and answers."
categories: [Spring Cloud]
---

# Spring Cloud
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

##  Introducing Spring Cloud


##  Spring Cloud

Spring team has integrated number of battle-tested open source projects from companies like Pivotal, Netflix into a Spring project known as Spring Cloud. Spring Cloud provides libraries & tools to quickly build some of the common design patterns of distributed system, including the following:

**Spring Cloud Patterns and Libraries**


| Category             | Pattern Name                                   | Spring Cloud Library                        |
| ---------------------- | ------------------------------------------------ | --------------------------------------------- |
| Development Patterns | Distributed/versioned configuration management | Spring Cloud Config Server                  |
|                      | Core Microservices Patterns                    | Spring Boot                                 |
|                      | Asynchronous/Distributed Messaging             | Spring Cloud Stream (AMQP and Kafka)        |
|                      | Inter-Service Communication                    | RestTemplate and Spring Cloud Feign         |
| Routing Patterns     | Service Registration & Discovery               | Spring Cloud Netflix Eureka & Consul        |
|                      | Service Routing/ API Gateway Pattern           | Spring Cloud Netflix Zuul                   |
| Resiliency Patterns  | Client side load balancing                     | Spring Cloud Netflix Ribbon                 |
|                      | Circuit Breaker & Fallback Pattern             | Spring Cloud Netflix Hystrix                |
|                      | Bulkhead pattern                               | Spring Cloud / Spring Cloud Netflix Hystrix |
| Logging Patterns     | Log Correlation                                | Spring Cloud Sleuth                         |
|                      | Microservice Tracing                           | Spring Cloud Sleuth/Zipkin                  |
| Security Patterns    | Authorization and Authentication               | Spring Cloud Security OAuth2                |
|                      | Credentials Management                         | Spring Cloud Security OAuth2/ JWT           |
|                      | Distributed Sessions                           | Spring Cloud OAuth2 and Redis               |

Spring Cloud makes it really easy to develop, deploy and operate JVM applications for the Cloud.

Different release trains in Spring Cloud at the time of writing this handbook are (newest to oldest) - Finchley, Edgware, Dalston and Camden. Spring Cloud is always used in conjunction with Spring Boot.

A bare minimum `build.gradle` for any Spring Cloud project will look like:

**build.gradle**

```properties
buildscript {
    ext {
        springBootVersion = '1.5.12.RELEASE'
    }
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}
apply plugin: 'java'
apply plugin: 'spring-boot'
dependencyManagement {
    imports {
        mavenBom ':spring-cloud-dependencies:Edgware.SR3'
    }
}
dependencies {
    compile ':spring-cloud-starter-config'
    compile ':spring-cloud-starter-eureka'
}

```

- Edgware.SR3 is the spring-cloud train version.
- Spring cloud dependencies (eureka client and config client)

And a minimal version of `spring-cloud` Application:

```java
@SpringBootApplication
@EnableDiscoveryClient
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}

```

- Enables spring-boot in your application.
- Enables discovery-client: a spring-cloud feature in your microservice that helps you discover other services in a given environment.



---

## Reference Links
- [Spring Cloud](http://projects.spring.io/spring-cloud/)