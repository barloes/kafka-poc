# Setting up connector using confluence base image

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
