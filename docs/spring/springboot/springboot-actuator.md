---
title: Spring Boot Actuator
hide:
  - tags

tags:
- Actuator


---

#  Spring Boot Actuator


---

##  Spring Boot Actuator


Spring Boot Actuator is a sub-project of Spring Boot. It provides a series of ready-to-use features that help you monitor and manage your Spring Boot application. Spring Boot Actuator is essential for understanding the state of your application running in production.

### Key Features

- **Health Checks:** Actuator includes a health indicator feature that shows application health information. It can be extended to show application-specific health data.
- **Metrics Collection:** It gathers and reports various metrics such as HTTP requests, database calls, and more, allowing for performance analysis.
- **Application Info:** Display general information about the application, such as Git commit information, build information, and more.
- **Custom Endpoints:** You can create custom endpoints to expose specific functionalities or information about your application.
- **Environment Details:** Provides details about the application's environment, including configuration properties, system properties, environment variables, and more.

### Enabling Spring Boot Actuator

To use Spring Boot Actuator, you need to add its dependency to your Spring Boot project. If you are using Maven, include the following in your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

For Gradle, add this to your `build.gradle`:

```groovy
implementation 'org.springframework.boot:spring-boot-starter-actuator'
```

### Accessing Actuator Endpoints

Once the dependency is added, Actuator endpoints can be accessed via HTTP or JMX. Many endpoints are available, such as `/actuator/health` for health checks and `/actuator/metrics` for metrics collection.

Here's an example of accessing the health endpoint:

```bash
curl http://localhost:8080/actuator/health
```

This command returns the health status of your application.

### Security Considerations

Actuator endpoints can expose sensitive information about your application. It is crucial to secure these endpoints, especially in production. Spring Boot allows you to restrict access to these endpoints using Spring Security.
 
Spring Boot Actuator is a powerful tool for monitoring and managing your Spring Boot applications. It provides insights into the application's performance, health status, and more, facilitating better operational and development practices.



### Adding Spring Boot Actuator

#### Step 1: Include Actuator Dependency

To integrate Spring Boot Actuator into your Spring Boot application, you must first add the Actuator starter dependency to your project's build configuration file. This can be done using Maven or Gradle, the two most common build tools for Java projects.

- **For Maven:**

Add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

- **For Gradle:**

Include this dependency in your `build.gradle`:

```groovy
implementation 'org.springframework.boot:spring-boot-starter-actuator'
```

#### Step 2: Configure Actuator Endpoints (Optional)

By default, Spring Boot Actuator exposes several endpoints, but you might want to enable additional endpoints or customize their security settings.

In your `application.properties` or `application.yml`, you can configure the endpoints. For example, to enable all endpoints, you could add:

```properties
management.endpoints.web.exposure.include=*
```

Be cautious with exposing all endpoints, as some can reveal sensitive information about your application. Always consider the security implications, especially in production environments.

#### Step 3: Accessing Actuator Endpoints

After adding the dependency (and optionally configuring the endpoints), you can access them via HTTP. For example, to check the health of your application, you might use:

```bash
curl http://localhost:8080/actuator/health
```

This command accesses the health endpoint, providing basic application health information.

#### Step 4: Secure Actuator Endpoints

It's crucial to secure your Actuator endpoints, especially if you enable sensitive ones. You can use Spring Security to restrict access to these endpoints. For example, you might configure HTTP basic authentication or integrate with OAuth2 for more robust security.

To secure endpoints with basic authentication, include the Spring Security dependency in your project and configure authentication in your security configuration class.
 

Integrating Spring Boot Actuator into your application provides valuable insights and management capabilities. It's straightforward to add with just a dependency and some optional configuration. Remember to secure your endpoints, particularly when deploying your application to a production environment, to protect sensitive information.

---

## Commonly Used Spring Boot Actuator Endpoints

Spring Boot Actuator provides a wide range of endpoints that offer various insights and management capabilities for your application. Below are some of the most commonly used endpoints and their purposes:

### 1. `/actuator/health`

- **Purpose:** Shows application health information. It provides a simple status (UP, DOWN, OUT_OF_SERVICE, UNKNOWN) to indicate if the application is running correctly. Can be extended to include checks for database connectivity, disk space, and custom health indicators.

### 2. `/actuator/info`

- **Purpose:** Displays arbitrary application information. This can include build version, description, and custom info contributors. It's often used to show application version at runtime, which can be helpful for debugging or audit purposes.

### 3. `/actuator/metrics`

- **Purpose:** Provides detailed metrics about the application. This endpoint can expose various system and application metrics such as JVM memory usage, system CPU usage, and custom metrics. It's invaluable for monitoring application performance and troubleshooting.

### 4. `/actuator/env`

- **Purpose:** Accesses the application's environment properties, including system properties, environment variables, configuration properties, and more. It's useful for debugging configuration issues and understanding the application's runtime environment.

### 5. `/actuator/loggers`

- **Purpose:** Allows viewing and modifying the logging level of application loggers. This endpoint is crucial for dynamically adjusting log levels to capture more detailed logs for troubleshooting without restarting the application.

### 6. `/actuator/threaddump`

- **Purpose:** Provides a dump of all threads in the application's JVM. It's a critical tool for diagnosing deadlock situations or understanding what the application is doing at a granular level.

### 7. `/actuator/heapdump`

- **Purpose:** Downloads a heap dump of the application’s JVM. Useful for analyzing memory usage and finding memory leaks. Note: This endpoint may not be enabled by default due to its potential impact on application performance.

### 8. `/actuator/auditevents`

- **Purpose:** Shows audit events information. This includes security-related events like login success and failure, which can be used for auditing and monitoring security aspects of the application.

### Security Considerations

While these endpoints provide valuable insights, they can also expose sensitive information about your application. Therefore, it's crucial to secure them, typically by limiting their exposure to authenticated users or by restricting access to specific IP addresses or networks.

### Customizing Endpoint Exposure

You can control which endpoints are exposed and through which medium (HTTP, JMX) by configuring the `management.endpoints.web.exposure.include` and `management.endpoints.web.exposure.exclude` properties in your `application.properties` or `application.yml`.

### Extending Actuator’s Capabilities

Beyond utilizing the commonly used endpoints, you can extend Spring Boot Actuator's capabilities in several ways to fit your specific needs:

### Creating Custom Endpoints

Spring Boot Actuator allows for the creation of custom endpoints. This feature can be particularly useful when you need to expose application-specific information or functionality through an Actuator-like interface. Custom endpoints can be created by implementing the `Endpoint` interface or, more commonly, by annotating a class with `@Endpoint`, `@ReadOperation`, `@WriteOperation`, or `@DeleteOperation` annotations depending on the type of operations you want to support.

### Customizing Health Indicators

While the `/actuator/health` endpoint provides basic health status, you can customize or add new health indicators to reflect the health status of other application components or external systems your application depends on. This is done by implementing the `HealthIndicator` interface and defining the health check logic that is relevant to your application.

### Integrating with External Monitoring Systems

Spring Boot Actuator’s metrics can be easily integrated with external monitoring systems like Prometheus, Grafana, or DataDog. This is facilitated through the Micrometer library, which Spring Boot Actuator uses for its metrics. Micrometer acts as a facade for various monitoring systems, allowing you to export metrics to your preferred monitoring solution with minimal configuration.

### Securing Actuator Endpoints

Security is a critical aspect of using Spring Boot Actuator, especially when deploying applications to production. Spring Security can be integrated to protect Actuator endpoints through authentication and authorization. For example, you might restrict sensitive endpoints to only be accessible by users with specific roles or permissions. Spring Boot also allows configuring endpoint security at a granular level, enabling different security requirements for different endpoints.

### Best Practices

- **Limit Exposure:** Only expose necessary endpoints and secure them appropriately. Use properties to include or exclude specific endpoints from being exposed over the web.
- **Monitor Access:** Keep an eye on the access logs for Actuator endpoints, particularly in production, to detect any unauthorized access attempts.
- **Regularly Update Dependencies:** Ensure that you are using the latest version of Spring Boot and Actuator to take advantage of security patches and new features.
- **Use HTTPS:** When exposing endpoints over the web, ensure that your application is configured to use HTTPS to encrypt the data in transit.




---

## Including or Excluding Actuator Endpoints

Controlling the exposure of Spring Boot Actuator endpoints is crucial for both security and performance. Spring Boot provides a straightforward way to include or exclude specific endpoints from being exposed. This can be done through properties in `application.properties` or `application.yml` configuration files.

#### Using `application.properties`

To include or exclude specific Actuator endpoints in your `application.properties`, you can use the following properties:

- **To Include Specific Endpoints:**

```properties
management.endpoints.web.exposure.include=health,info
```

This configuration will expose only the `health` and `info` endpoints. All other endpoints will not be accessible.

- **To Exclude Specific Endpoints:**

```properties
management.endpoints.web.exposure.exclude=env,beans
```

This configuration will prevent the `env` and `beans` endpoints from being exposed, while all other endpoints will be available by default.

#### Using `application.yml`

Alternatively, if you prefer using `application.yml` for configuration, the syntax would be slightly different:

- **To Include Specific Endpoints:**

```yaml
management:
  endpoints:
    web:
      exposure:
        include: health,info
```

- **To Exclude Specific Endpoints:**

```yaml
management:
  endpoints:
    web:
      exposure:
        exclude: env,beans
```

#### Combining Include and Exclude

When both `include` and `exclude` properties are specified, `exclude` takes precedence. This means that if an endpoint is listed in both include and exclude, it will not be exposed.

#### Fine-Grained Exposure Control

Spring Boot Actuator also allows for more granular control over endpoint exposure:

- **Expose All Endpoints:**

To expose all available endpoints:

```properties
management.endpoints.web.exposure.include=*
```

- **Combining Wildcards and Specific Exclusions:**

You can combine wildcard inclusion with specific exclusions for more fine-grained control:

```properties
management.endpoints.web.exposure.include=*
management.endpoints.web.exposure.exclude=env,beans
```

This setup exposes all endpoints except for `env` and `beans`.

#### Security Considerations

While exposing endpoints can provide valuable insights and management capabilities, it's essential to consider the security implications. Always ensure that sensitive endpoints, especially those that can alter state or provide detailed application internals (like `env`, `heapdump`), are protected appropriately, typically through Spring Security.

 

Configuring which Actuator endpoints are exposed or hidden is a straightforward process in Spring Boot, offering flexibility to balance between transparency, functionality, and security. Properly managing endpoint exposure is a key part of maintaining a secure and efficient production environment for your Spring Boot applications.


---

## Integrating with External Monitoring Systems

Spring Boot Actuator's metrics feature can be seamlessly integrated with external monitoring systems such as Prometheus and Grafana, providing a powerful toolset for observing and understanding the behavior of your application in real-time. This integration is facilitated through the Micrometer library, which Spring Boot uses for its metrics collection. Micrometer acts as an instrumentation facade, offering a vendor-neutral interface for collecting metrics, which can then be exported to various monitoring systems.

#### Integration with Prometheus

Prometheus is a popular open-source monitoring and alerting toolkit that is particularly well-suited for collecting time-series data. Here’s how you can integrate Spring Boot Actuator with Prometheus:

1. **Add Prometheus Dependency:**

First, add the Micrometer Prometheus registry dependency to your project. For Maven, include this in your `pom.xml`:

```xml
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
    <version>latest.version</version>
</dependency>
```

For Gradle, add this to your `build.gradle`:

```groovy
implementation 'io.micrometer:micrometer-registry-prometheus:latest.version'
```

2. **Configure Actuator to Expose Prometheus Endpoint:**

Ensure that your `application.properties` or `application.yml` includes the Actuator Prometheus endpoint:

```properties
management.endpoints.web.exposure.include=prometheus
```

This configuration exposes the `/actuator/prometheus` endpoint, which Prometheus can scrape to collect metrics.

3. **Configure Prometheus to Scrape Your Application:**

You'll need to configure Prometheus to scrape metrics from your application. This is typically done in the Prometheus configuration file (`prometheus.yml`), where you add your application as a target:

```yaml
scrape_configs:
  - job_name: 'spring-application'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['localhost:8080']
```

#### Visualization with Grafana

Grafana is a popular open-source platform for monitoring and observability that integrates well with Prometheus, allowing you to visualize your metrics through dashboards. Here’s how to visualize your Spring Boot metrics in Grafana:

1. **Set Up Grafana and Add Prometheus as a Data Source:**

After installing Grafana, add Prometheus as a data source through the Grafana UI by providing the URL to your Prometheus server.

2. **Create or Import Dashboards:**

You can create custom dashboards in Grafana or import existing ones. The Grafana community has many pre-built dashboards for visualizing metrics from Prometheus, including dashboards specifically designed for Spring Boot applications.

3. **Visualize Your Application Metrics:**

Once your dashboard is set up, you can start visualizing the metrics collected from your Spring Boot application. This can include JVM metrics, application throughput, response times, and custom application metrics.





---

## Strategies for Scaling Monitoring in Microservices

In a microservices architecture, effectively monitoring applications becomes challenging due to the distributed nature of services. Spring Boot Actuator, when used in conjunction with other tools and practices, can facilitate comprehensive and scalable monitoring solutions. Here are some strategies to consider:

#### 1. Centralized Logging

- **Use Centralized Log Management:** Tools like ELK Stack (Elasticsearch, Logstash, Kibana) or Fluentd can aggregate logs from multiple services in a centralized location. Spring Boot applications can be configured to send logs to these tools, making it easier to search and analyze logs across services.

#### 2. Distributed Tracing

- **Implement Distributed Tracing:** Solutions like Zipkin, Jaeger, or Spring Cloud Sleuth can be integrated with Spring Boot applications to track requests across service boundaries. This helps in understanding the flow of requests and identifying bottlenecks or failures in the system.

#### 3. Metrics Aggregation

- **Aggregate Metrics:** Use Prometheus with Micrometer in Spring Boot to collect and aggregate metrics from all microservices. Prometheus can scrape metrics exposed by the Actuator `/actuator/prometheus` endpoint of each service.

#### 4. Dynamic Service Discovery for Monitoring

- **Leverage Service Discovery:** In a microservices architecture, services can dynamically scale in and out. Integrating your monitoring tools with service discovery mechanisms (like Eureka, Consul, or Kubernetes services) ensures that your monitoring setup automatically adjusts to the changing landscape of your services.

#### 5. Unified Dashboard for Metrics Visualization

- **Use Grafana for Unified Dashboards:** Grafana can connect to multiple data sources, including Prometheus, to create comprehensive dashboards that visualize metrics from all your microservices. This unified view is crucial for monitoring the health and performance of the entire system.

#### 6. Health Check Aggregation

- **Aggregate Health Checks:** Tools like Spring Boot Admin can aggregate health indicators from the `/actuator/health` endpoint of each microservice, providing a holistic view of the system’s health. This can be crucial for quickly identifying and addressing issues in a specific service.

#### 7. Alerting and Notification

- **Configure Alerting:** Integrate alerting tools with your monitoring setup to receive notifications about critical issues. Prometheus Alertmanager, integrated with communication platforms like Slack or email systems, can automate alerts based on specific metrics thresholds or service health status.

#### 8. Automate Response Mechanisms

- **Automation for Scaling and Healing:** Use Kubernetes or other orchestration tools to automatically scale services based on metrics thresholds or to perform self-healing actions in response to health check failures.

#### 9. Security and Access Management

- **Secure Monitoring Tools:** Ensure that access to monitoring tools and data is secured and managed, given the sensitive nature of the information they hold. Implement access controls and audit logs to monitor who accesses the monitoring data.

#### 10. Regular Review and Optimization

- **Continuously Optimize Monitoring Setup:** Regularly review your monitoring strategies and configurations to ensure they are aligned with the evolving architecture and business requirements. This includes optimizing alert thresholds, updating dashboards, and refining log aggregation policies.

 

Effective monitoring in a microservices architecture requires a combination of tools, practices, and strategies that work together to provide a comprehensive view of the system’s health and performance. By leveraging Spring Boot Actuator in conjunction with centralized logging, distributed tracing, metrics aggregation, and dynamic service discovery, teams can create a scalable and resilient monitoring solution that supports the complexity and dynamism of microservices-based applications.


---

---




