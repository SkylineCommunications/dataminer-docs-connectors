---
uid: Connector_help_Techex_Darwin
---

# Techex Darwin

The Techex Darwin connector can display configuration via the REST API and metrics by consuming kafka messages. Designed for hybrid and pure Cloud software workflows, tx darwin offers a secure and flexible live media processing, transport & monitoring micro-service based platform

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |1.4.0         |


### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Initialization

For the REST API to work the **Username** and **Pasword** needs to be configured in the General Page.
For the connector to start receiving Kafka messages the following parameters need to be configured.
    -**Bootstrap Server**
    -**Port**
    -**Client ID** (Optional)
    -**Group ID** (Optional)

Also an entry in the **Kafka Topic Subscriptions** needs to be created specifying the topic name.


### Redundancy

There is no redundancy defined.

## How to use

To poll REST API data only the username and password needs to be filled in. After that the commands getting send and their frequency can be controlled using the **Poll Manager Table**.   

To subscribe to start receiving Kafka messages after configurring the parameters above clicking on the button **Consume** will start the conenction, The **Connection** parameter in the same page can be use to see if this operation worked. 

Note:
-For Kafka messages to work the **Modules** command from the REST API needs to be enabled to populate the **Schema Modules** which this table then controls individual processing of kafka messages for each modules and their frequency.  


### Layout

The conenctor is splited in two main parts Config and Metrics. Any table that ends with config is information comming from the REST API, and metrics is anything coming from Kafka.


