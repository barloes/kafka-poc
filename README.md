# Starting up
```
docker-compose up
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

# Bitnami kafka bin path
```
/opt/bitnami/kafka/bin
```

Reference
- https://github.com/ueisele/kafka-images/blob/main/examples/kraft/cluster-shared-mode/docker-compose.yaml