# Confluent Kafka REST APIs

```shell
java -Xmx256M -server -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:InitiatingHeapOccupancyPercent=35 -XX:+ExplicitGCInvokesConcurrent -Djava.awt.headless=true -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Dlog4j.configuration=file:C:/Temp/confluent-7.3.2/etc/kafka-rest/log4j.properties -cp C:/Temp/confluent-7.3.2/kafka-rest/target/kafka-rest-*-development/share/java/kafka-rest/*;C:/Temp/confluent-7.3.2/share/java/confluent-security/kafka-rest/*;C:/Temp/confluent-7.3.2/share/java/confluent-common/*;C:/Temp/confluent-7.3.2/share/java/confluent-telemetry/*;C:/Temp/confluent-7.3.2/share/java/rest-utils/*;C:/Temp/confluent-7.3.2/share/java/kafka-rest-bin/*;C:/Temp/confluent-7.3.2/share/java/kafka-rest-lib/*;C:/Temp/confluent-7.3.2/share/java/monitoring-interceptors/* io.confluent.kafkarest.KafkaRestMain
```
