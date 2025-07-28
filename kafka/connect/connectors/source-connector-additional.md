## Additional configuration options
```bash
curl -X POST http://localhost:8081/connectors -H 'Content-Type: application/json' -d'
{
	"name": "pg-payment-cart-source",
	"config": {
	    //"topic.prefix": "pg-",
        //"mode": "timestamp",
        //"mode": "timestamp+incrementing",
        //"timestamp.column.name": "updated_at",
        //"poll.interval.ms": "10000",
        //"batch.max.rows": "5000"
        // ... other configuration options
	}
}'
```