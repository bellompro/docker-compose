# A request to create a source connector
```bash
curl -X POST http://localhost:8081/connectors -H 'Content-Type: application/json' -d'
{
	"name": "pg-payment-cart-source",
	"config": {
	  "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
	  "tasks.max": "1",
	  "connection.url": "jdbc:postgresql://postgres:5432/postgres",
	  "connection.user": "root",
	  "connection.password": "postgres",
	  "mode": "incrementing",
	  "incrementing.column.name": "id",
	  "table.whitelist": "payment,cart"
	}
}'
```