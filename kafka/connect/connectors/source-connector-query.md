# A request to create a source connector with a custom query
```bash
curl -X POST http://localhost:8081/connectors -H 'Content-Type: application/json' -d'
{
	"name": "pg-payment-source",
	"config": {
	  "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector",
	  "tasks.max": "1",
	  "connection.url": "jdbc:postgresql://localhost:5432/postgres",
	  "connection.user": "postgres",
	  "connection.password": "mypassword",
	  "mode": "incrementing",
	  "incrementing.column.name": "id",
	  "topic.name": "payment-with-carts",
	  "query": "SELECT *, COALESCE(( SELECT json_agg(cart_row) FROM ( SELECT * FROM cart c WHERE c.payment_id = p.id ) AS cart_row ), '[]') AS carts FROM payment p;"
	}
}'
```