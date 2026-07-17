---
uid: Connector_help_Generic_KAFKA_Producer
---

# Generic KAFKA Producer

## About

### Apache Kafka

Apache Kafka is an open-source, distributed event streaming platform used by thousands of organizations for high-performance data pipelines, streaming analytics, and event-driven integrations. It is built around a simple but powerful idea: applications publish streams of **events** (records) that are durably stored and that can be read by any number of independent applications, in real time or later.

A Kafka deployment runs as a cluster of one or more servers that can span multiple data centers or cloud regions. Within that cluster:

- **Brokers** form the storage layer, durably persisting events and replicating them for fault tolerance.
- **Producers** are client applications that publish (i.e., write) events to Kafka.
- **Consumers** are client applications that subscribe to (i.e., read and process) those events.

Events are organized into **topics**, which are durable, append-only logs that act like categories or folders. Producers and consumers are fully decoupled: a producer never needs to know who will consume its data, and consumers can join, leave, or replay a topic at any time without affecting the producer. This decoupling is what makes Kafka so well suited to integrating many systems reliably and at scale.

### DataMiner as a Kafka Producer

The **Generic KAFKA Producer** turns DataMiner into a first-class Kafka producer, allowing you to stream operational data directly from your DataMiner System and into your organization's Kafka-based data platform. Instead of locking alarms and performance metrics inside DataMiner, you can publish them as structured events that data lakes, analytics engines, machine-learning pipelines, dashboards, and downstream microservices can consume independently.

Two kinds of data can be published to a broker:

- **Alarms**: Alarm information received via SNMP inform/trap forwarding is converted into JSON messages and sent to a configurable alarm topic — ideal for feeding centralized incident management, correlation, or reporting systems.
- **Parameter values**: Live parameter values from any element or enhanced service in the DataMiner System are polled and forwarded to a topic, letting you stream real-time telemetry into big-data and analytics platforms.

Because everything is configured from the element's UI — the target topics, partition keys, authentication, serialization format, and exactly which alarms and parameters to forward — you can set up a robust DataMiner-to-Kafka integration without writing any custom code.

## Key Features

- **Alarm forwarding**: Forward SNMP inform/trap alarm data, received via SNMP Manager forwarding, to a Kafka topic, with configurable bindings, a configurable partition key, and buffering of pending alarms while the broker is unreachable.
- **Parameter forwarding**: Poll and forward parameter values from any element or enhanced service to a Kafka topic on a configurable interval, optionally only sending a value when it changes, with per-row target topics.
- **Flexible broker security**: Connect to the broker using SASL/PLAIN (over TLS or plaintext), mutual TLS (SSL), or OAuth 2.0 / OIDC bearer-token authentication.
- **AVRO serialization**: Optionally serialize messages as AVRO through a Confluent Schema Registry, with a schema loaded from the registry or a local `.avsc` file.
- **CSV import/export**: Import alarm bindings and parameter configurations from CSV files, and forward historical Alarm Console alarms from a CSV export.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Generic_KAFKA_Producer_Technical).
