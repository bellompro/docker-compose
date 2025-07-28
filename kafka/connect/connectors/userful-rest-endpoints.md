# You can monitor, pause, and restart connectors—all via the API.
The REST API is the primary way to interact with Kafka Connect. It allows you to manage connectors, tasks, and configurations.
# Useful REST Endpoints
## Set base URL
```bash
#!/bin/bash
baseUrl=http://localhost:8081
```
## List all connectors
```bash
curl -X GET $baseUrl/connectors
```
## Create a new connector
```bash
curl -X POST $baseUrl/connectors -H 'Content-Type: application/json' -d'
{
    "name": "<connector-name>",
    "config": {
        // Create configuration options
    }
}'
```
## Get connector configuration
```bash
curl -X GET $baseUrl/connectors/<connector-name>/config
```
## Update connector configuration
```bash
curl -X PUT $baseUrl/connectors/<connector-name>/config -H 'Content-Type: application/json' -d'
{
    "config": {
        // Updated configuration options
    }
}'
```
## Delete Source Connector
```bash
curl -X DELETE $baseUrl/connectors/pg-payment-cart-source
```
## Delete Sink Connector
```bash
curl -X DELETE $baseUrl/connectors/es-payment-sink
```
## Connector Status 
```bash 
curl -X GET $baseUrl/connectors/<connector-name>/status
```
## Pause Connector
```bash
curl -X PUT $baseUrl/connectors/<connector-name>/pause
```
## Resume Connector
```bash
curl -X PUT $baseUrl/connectors/<connector-name>/resume
```
## Restart Connector
```bash
curl -X POST $baseUrl/connectors/<connector-name>/restart
```
## List all tasks
```bash
curl -X GET $baseUrl/connectors/<connector-name>/tasks
```
## Restart a specific task
```bash
curl -X POST $baseUrl1/connectors/<connector-name>/tasks/<task-id>/restart
```

## These are Elasticsearch-specific endpoints
## List all Elasticsearch indices
```bash
curl -X GET -u elastic:elasticsearch http://localhost:9200/_cat/indices?v
```
## Get Elasticsearch index mapping
```bash
curl -X GET http://elasticsearch:9200/<index-name>/_mapping
```
## Get Elasticsearch index settings
```bash
curl -X GET http://elasticsearch:9200/<index-name>/_settings
```
## Delete Elasticsearch index
```bash
curl -X DELETE http://elasticsearch:9200/<index-name>
```
## Create Elasticsearch index with custom settings
```bash
curl -X PUT http://elasticsearch:9200/<index-name> -H 'Content-Type: application/json' -d'
{
    "settings": {
        "number_of_shards": 1,
        "number_of_replicas": 1
    },
    "mappings": {
        "properties": {
            "field1": { "type": "text" },
            "field2": { "type": "keyword" }
        }
    }
}'
```
## Search Elasticsearch index
```bash
curl -X GET http://elasticsearch:9200/<index-name>/_search -H 'Content-Type: application/json' -d'
{
    "query": {
        "match_all": {}
    }
}'
```