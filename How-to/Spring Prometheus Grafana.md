# Spring Boot
## Configuration
### pom.xml
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>
```

### application.properties
```properties
# management
management.info.env.enabled=true
management.info.java.enabled=true
management.info.build.enabled=true
management.info.git.enabled=true
management.info.git.mode=full
management.endpoints.web.exposure.include=*
management.endpoint.health.show-details=always
management.metrics.tags.application=${spring.application.name}
management.endpoint.logfile.external-file=logs/${spring.application.name}.log
```

## Micrometer custom metrics
### One

```java
@Component
public class Scheduler {

  private final AtomicInteger testGauge;
  private final Counter testCounter;

  public Scheduler(MeterRegistry meterRegistry) {
    // Counter vs. gauge, summary vs. histogram
    // https://prometheus.io/docs/practices/instrumentation/#counter-vs-gauge-summary-vs-histogram
    testGauge = meterRegistry.gauge("custom_gauge", new AtomicInteger(0));
    testCounter = meterRegistry.counter("custom_counter");
  }

  @Scheduled(fixedRateString = "1000", initialDelayString = "0")
  public void schedulingTask() {
    testGauge.set(Scheduler.getRandomNumberInRange(0, 100));

    testCounter.increment();
  }

  private static int getRandomNumberInRange(int min, int max) {
    if (min >= max) {
      throw new IllegalArgumentException("max must be greater than min");
    }

    Random r = new Random();
    return r.nextInt((max - min) + 1) + min;
  }
}
```

```bash
http GET "http://localhost:8080/actuator/prometheus" | grep custom
# HELP custom_gauge
# TYPE custom_gauge gauge
custom_gauge 29.0
# HELP custom_counter_total
# TYPE custom_counter_total counter
custom_counter_total 722.0
```
### Two

```java
@Configuration
@EnableAspectJAutoProxy
public class AutoTimingConfig {
    @Bean
    public TimedAspect timedAspect(MeterRegistry registry) {
        return new TimedAspect(registry);
    }
}

@Service
public class TestService {
    @Timed
    public void testMethod() {
        // do somthing
    }
}
```

```properties
# counter
method_timed_seconds_count{application="test-app",class="com.sbtele.TestService",exception="none",method="testMethod"}
# work timer
method_timed_seconds_sum{application="test-app",class="com.sbtele.TestService",exception="none",method="testMethod"}
# max work time
method_timed_seconds_max{application="test-app",class="com.sbtele.TestService",exception="none",method="testMethod"}
```

### Three

```java
@Service
public class TestService {
    @Autowired
    private MeterRegistry meterRegistry;
    
    public TestObject testMethod() {   
        AtomicReference<TestObject> testObject = new AtomicReference<>();
        // timer
        meterRegistry.timer("method.timed", "method", "testMethod").record(() -> {
            testObject.set(new TestObject()); // get result
        });
        return testObject.get();
    }
    
    public TestObject testMethod2() {
        long start = System.currentTimeMillis();
        Timer timer = meterRegistry.timer("method.timed", "method", "testMethod2");
    
        TestObject testObject = new TestObject(); // get result

        // timer
        timer.record(System.currentTimeMillis() - start, TimeUnit.MILLISECONDS);
        // counter (if need separately)
        meterRegistry.counter("method.counted", "method", "testMethod2").increment();

        return testObject;
    }
}
```

## Micrometer built-in metrics

```java
@Configuration
public class Config {
    @Bean
    public TimedAspect timedAspect(MeterRegistry registry) {
        return new TimedAspect(registry);
    }

    @Bean
    CountedAspect countedAspect(MeterRegistry registry) {
        return new CountedAspect(registry);
    }
}
```

```java
@Timed(value = "timed.test", description = "Test method call time")
public void test1() {
    // some functionality
}
@Counted(value = "counted.success.test", description = "Test method call counter")
public void test2() {
    // some functionality
}
```

# Prometheus
## prometheus.yml

```yml
global:
    scrape_interval: 10s # How frequently to scrape targets by default
  
scrape_configs:
    - job_name: 'spring_micrometer'         # The job name is assigned to scraped metrics by default.
      metrics_path: '/actuator/prometheus'  # The HTTP resource path on which to fetch metrics from targets.
      scrape_interval: 5s                   # How frequently to scrape targets from this job.
      static_configs:                       # A static_config allows specifying a list of targets and a common label set for them
        - targets: ['172.20.4.2:8080']
```
```docker run -d -p 9090:9090 -v /mnt/c/Temp/000/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus```

http://localhost:9090

# Grafana

```docker run --net=host -d -p 3000:3000 grafana/grafana```

http://localhost:3000 admin/admin

And need add Prometheus http://localhost:9090 to Grafana Data Sources.

Then import and configure dashboard https://grafana.com/grafana/dashboards/4701

## Sources

https://habr.com/ru/company/otus/blog/650871

https://stackoverflow.com/questions/54776604/how-can-i-change-the-datasource-for-a-grafana-dashboard

https://qna.habr.com/q/299390

https://serveradmin.ru/obnovlenie-grafana
