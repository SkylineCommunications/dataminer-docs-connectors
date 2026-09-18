---
uid: Connector_help_Generic_KAFKA_Consumer
description: "Learn how to use the Generic KAFKA Consumer connector to consume Kafka topics and export messages for DataMiner workflows."
---

# Generic KAFKA Consumer

## About

The **Generic KAFKA Consumer** connector integrates Apache Kafka data streams with DataMiner. It connects to one or more configured brokers, consumes messages from selected topics, and exports the received data as compressed GZ files containing JSON.

The connector uses a virtual connection, so no connection details are required when creating the DataMiner element. Broker, topic, authentication, schema registry, and export settings are configured in the element after creation.

## Key Features

- Consumes multiple Kafka topics through one or more configured brokers.
- Supports configurable subscription intervals and poll durations per topic.
- Supports unsecured, SSL, SASL/SSL, SCRAM, and OAuth-based authentication scenarios.
- Supports string messages and Avro messages through a Confluent Schema Registry.
- Exports topic data as compressed GZ files to local or remote storage.
- Provides polling-buffer visibility, automatic cleanup, file-retention settings, and optional InterApp notifications.

## Use Cases

### Bring Kafka Event Data into DataMiner Workflows

**Challenge**: Operational data is published to Kafka but must be made available to DataMiner connectors, automation scripts, or other processing workflows.

**Solution**: Configure the relevant brokers and topics in the connector. The connector consumes the messages and exports them as compressed JSON data files.

**Benefit**: Kafka data becomes available to DataMiner-based monitoring and orchestration without requiring each downstream workflow to implement its own Kafka client.

### Consume Secured Enterprise Kafka Streams

**Challenge**: Kafka environments can require SSL certificates, SASL credentials, OAuth, or Schema Registry authentication.

**Solution**: Configure the required security method and credentials on the Authentication, OAuth, and Schema Registry pages.

**Benefit**: The connector can be adapted to different enterprise Kafka security configurations while keeping consumption and export behavior consistent.

### Control Data Volume and Retention

**Challenge**: High-volume topics can create large exports and accumulated files.

**Solution**: Configure topic polling, maximum export size, export location, and housekeeping retention settings.

**Benefit**: Operators can balance data freshness, file size, storage usage, and downstream processing requirements.

## Technical Reference

For configuration details and operating instructions, refer to the [technical documentation](xref:Connector_help_Generic_KAFKA_Consumer_Technical).
