# A request to create a sink connector
```bash
curl -X POST http://localhost:8081/connectors -H 'Content-Type: application/json' -d'
{
    "name": "es-payment-sink",
    "config": {
        "connector.class": "io.confluent.connect.elasticsearch.ElasticsearchSinkConnector",
        "topics": "payment,cart",
        "connection.url": "http://elasticsearch:9200",
        "connection.username": "elastic",
        "connection.password": "elasticsearch",
        "type.name": "_doc",
        "key.ignore": true,
        "schema.ignore": true,
        "value.converter": "org.apache.kafka.connect.json.JsonConverter",
        "value.converter.schemas.enable": "false",
        "validate.indices.exists": "false",
        "use.data.stream": "false",
        "behavior.on.malformed.documents": "warn",
        "tasks.max": "1"
    }
}'
```