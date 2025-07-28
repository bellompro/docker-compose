# Installing Confluent Hub Connectors
Confluent Hub connectors can be installed using the `confluent-hub` CLI tool. The tool can be used to download and install connectors from the Confluent Hub repository. 
For more information, refer to the [Confluent Hub CLI documentation](https://docs.confluent.io/platform/current/connect/devguide/installing.html#confluent-hub-cli).

# Example: Installing the JDBC Source Connector
To install the JDBC Source Connector, you can use the following command:
```bash
confluent-hub install confluentinc/kafka-connect-jdbc:10.8.2 \
--component-dir /connect-plugins/kafka-connect-jdbc \
--worker-configs /tmp/dummy.properties
```
# Example: Installing the Elasticsearch Sink Connector
To install the Elasticsearch Sink Connector, you can use the following command:
```bash
confluent-hub install confluentinc/kafka-connect-elasticsearch:15.0.0 \
--component-dir /connect-plugins/kafka-connect-elasticsearch \
--worker-configs /tmp/dummy.properties
```