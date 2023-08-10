# Starting up
```
docker-compose -f kafka/docker-compose.yml up
docker-compose -f up mysql/docker-compose.yml
docker-compose -f up connector/docker-compose.yml
```
# create connector for jdbc source
```
curl -X POST -H "Content-Type: application/json" --data '{
  "name": "jdbc-source-source",
  "config": {
    "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
    "connection.url": "jdbc:mysql://mysql:3306/example",
    "connection.user": "root",
    "connection.password": "example",
    "table.whitelist": "person",
    "topic.prefix": "jdbc-",
    "poll.interval.ms": "5000",
    "mode":"incrementing",
    "incrementing.column.name":"id"
  }
}' http://localhost:8083/connectors
```
# inspect changes inside kafdrop
```
http://localhost:9001/topic/jdbc-person/
```


# Create topic
- create topic quickstart-events on kafka-1
```
kafka-topics --create --topic quickstart-events --bootstrap-server localhost:39092
```

# Producer
- producer on topic quickstart-events on kafka-1
```
kafka-console-producer --topic quickstart-events --bootstrap-server localhost:39092

```

# Consumer
- consumer on topic quickstart-events on kafka-2
```
kafka-console-consumer --topic quickstart-events --from-beginning --bootstrap-server localhost:29092
```

# Exposed port (local)
- 29092 (kafka-2)
- 39092 (kafka-1)
- 3307 (mysql) user: root password: example
- 9001 (kafdrop)
- 8083 (connector)

# Bitnami kafka bin path
```
/opt/bitnami/kafka/bin
```

# Connecting to local environment from docker

```
jdbc:mysql://host.docker.internal:3306/jaas?useUnicode=true&characterEncoding=utf8"
```

Reference
- https://github.com/ueisele/kafka-images/blob/main/examples/kraft/cluster-shared-mode/docker-compose.yaml
- https://docs.docker.com/compose/install/linux/