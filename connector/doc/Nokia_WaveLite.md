---
uid: Connector_help_Nokia_WaveLite
---

# Nokia WaveLite

The Nokia WaveLite connector allows you to monitor the device of the same name, focusing on the interfaces details, the physical entities present in the device, alarms, and the corresponding configuration. The device itself is an aggregator of enterprise services over optical networks.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection. This is the main connection used to retrieve all the data. It requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

This connector is mainly intended for monitoring purposes. Across the whole connector, there are some parameters that you can modify according to your preferences. Ideally, the connector should be used with alarm and trend templates to enable alarm monitoring and trending of the parameters.
