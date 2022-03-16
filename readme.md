# Readme

Setup:
```
docker compose up
```

Create topic for debezium history:
```
kafka_2.13-2.8.1/bin/kafka-topics.sh --bootstrap-server localhost:9092 --topic "debezium.mydb.history" --create
```

## kafka-connect

Delete connector
```
curl -X DELETE -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/my-test-debezium
```

List connectors
```
curl -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/
```

Create/Update connector:
```
curl -X PUT -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/my-test-debezium/config -d"$(cat debezium-demo.json)"
```

Restart connector
```
curl -X POST -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/my-test-debezium/restart
```

Status:
```
curl -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/my-test-debezium/status
```
