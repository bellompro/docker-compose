## These are Elasticsearch-specific endpoints
## List all Elasticsearch indices
## Set base URL
```bash
#!/bin/bash
esBaseUrl=http://localhost:9200
```
## List all Elasticsearch indices
```bash
curl -X GET -u elastic:elasticsearch $esBaseUrl/_cat/indices\?v
```
## Search Payment index
```bash
curl -X GET  -u elastic:elasticsearch $esBaseUrl/payment/_search -H 'Content-Type: application/json' -d'
{
    "query": {
        "match_all": {}
    }
}'
```
## Search Cart index
```bash
curl -X GET  -u elastic:elasticsearch $esBaseUrl/cart/_search -H 'Content-Type: application/json' -d'
{
    "query": {
        "match_all": {}
    }
}'
```
## Get Elasticsearch index mapping
```bash
curl -X GET  -u elastic:elasticsearch $esBaseUrl/payment/_mapping
```
## Get Elasticsearch index settings
```bash
curl -X GET  -u elastic:elasticsearch $esBaseUrl/payment/_settings
```
## Delete Elasticsearch index
```bash
curl -X DELETE  -u elastic:elasticsearch $esBaseUrl/cart
```
## Create Elasticsearch index with custom settings
```bash
curl -X PUT  -u elastic:elasticsearch $esBaseUrl/cart -H 'Content-Type: application/json' -d'
{
  "settings": {
    "number_of_shards": 1
  },
  "mappings": {
    "properties": {
      "dummy": { "type": "keyword" }
    }
  }
}'
```