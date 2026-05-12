---
uid: Connector_help_Generic_MQTT_Client_Technical
---

# Generic MQTT Client

## About

The Generic MQTT Client connector enables DataMiner to communicate with MQTT broker. It allows users to establish a connection to a broker, subscribing to selected topics to receive messages in real time, and publishing messages to specified topics.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **Element Configuration** page, configure the MQTT broker connection by specifying the following parameters:

- **Broker Hostname**
- **Broker Hostname Port**
- **Broker Credentials**

The broker credentials are mandatory and must be configured in order to establish a connection to the MQTT broker. Once the required settings have been configured, click the **Connect** button to establish communication with the MQTT broker.

## How to Use

### General and Broker Statistics

The **General** and **Broker Statistics** pages display the current connection status and general broker statistics. This provides an overview of the MQTT connection and broker activity.

### Messages

The **Messages** page contains a table listing all received MQTT messages. This includes the topic, payload, and timestamp for each message.
**Cleanup Configuration** subpage allows users to configure automatic cleanup of the **Received Messages** table. This includes specifying the maximum number of rows to retain and defining the maximum age of messages before they are automatically removed.

### Topics

The **Topics** page allows you to define the MQTT topics you want to subscribe to in order to receive incoming messages from the broker.

### Publish Data

The **Publish Data** page allows users to publish MQTT messages directly to the broker by specifying a target topic and the message payload.