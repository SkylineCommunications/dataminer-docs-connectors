---
uid: Connector_help_Ziggo_Kafka_Producer
---

# Ziggo Kafka Producer

The **Ziggo Kafka Producer** is a DataMiner connector that bridges the DataMiner offload database to an Apache Kafka cluster. It continuously scans one or two redundant SMB/CIFS shared folders for DataMiner trending offload CSV files, enriches every data point with live element metadata, and publishes the result as a JSON message to a configurable Kafka topic.

This connector enables downstream analytics, data lake ingestion, or real-time dashboarding pipelines to consume structured DataMiner telemetry data with no custom scripting or middleware required.

## Key Features

- **Automated offload file ingestion** — scans configured shared network folders every 10 seconds and processes new CSV files as soon as they appear.
- **Enriched JSON messages** — each offload data point is transformed into a rich JSON payload carrying the element name, DataMiner location, protocol name, element type, element state, parameter unit, and resolved discreet display values alongside the raw measured value and timestamp.
- **Apache Kafka publishing** — uses the Confluent Kafka library to publish messages to a named topic across one or more configurable broker endpoints.
- **SASL/PLAIN + optional SSL/TLS** — supports username/password authentication and SASL_SSL when a CA certificate path is provided.
- **LZ4 message compression** — reduces broker network and storage overhead with transparent compression.
- **Redundant folder failover** — two independent shared folder paths can be configured so that processing continues if one share is unreachable.
- **Per-directory publish scheduling** — each discovered subdirectory can be individually enabled or disabled, and its push interval is independently tunable (minimum 5 seconds).
- **Backlog visibility** — the **Files to Process** counter per directory is continuously updated and can be alarmed on.
- **Built-in error counters** — separate counters for parse-level errors and file-level processing errors surface problems directly in the element without requiring log file investigation.
- **DMS metadata caching** — element and parameter metadata is cached locally to minimise internal DataMiner API calls, with configurable refresh intervals.

## Configuration

See [Ziggo Kafka Producer — Technical](xref:Connector_help_Ziggo_Kafka_Producer_Technical).
