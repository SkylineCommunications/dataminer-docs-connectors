---
uid: Connector_help_Druid_Raemis
---

# Druid Raemis

Raemis is a technology platform by Druid Software that harnesses 5G, 4G, 3G, 2G, and Wi-Fi radios to implement standalone cellular core network solutions.

The Druid Raemis connector monitors this platform, by enlisting active alarms and also implementing a heartbeat mechanism that evaluates the liveliness of the Raemis platform.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware  |
|---------|---------------------|
| 1.0.0.x | 5.2.6.0-1, rd974ae4 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

#### SNMP Connection - Traps

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

For the HTTP connection, you need to configure the API authentication: go the **General** page, and configure the **Username** and **Password**.

On that same page, you can also configure the proxy server.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **Active Alarms** table on the Alarms page fetches the information from the REST API.

The **heartbeat mechanism** is based on receiving a specific, periodic SNMP trap (heartbeat). If the time between heartbeats is greater than the configured Heartbeat Delay parameter, an alarm is raised (with the Heartbeat Status parameter).
