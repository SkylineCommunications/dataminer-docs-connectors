---
uid: Connector_help_Druid_Raemis
---

# Druid Raemis

Raemis is a technology platform by Druid Software that harnesses 5G, 4G, 3G, 2G, and Wi-Fi radios to implement standalone cellular core network solutions.

The Druid Raemis connector monitors the platform through active alarms and SNMP heartbeat traps. It also collects MGW control flow statistics, including ingress, egress, and dropped traffic counters.

## About

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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The **Active Alarms** table on the **Alarms** page displays alarms retrieved from the REST API.

The connector monitors platform availability using periodic SNMP heartbeat traps. If the time between heartbeats exceeds **Heartbeat Delay**, an alarm is raised on **Heartbeat Status**.

The **Flow Stats** page displays MGW control flow statistics, including ingress, egress, and dropped packet and octet counts. Use **Polling Configuration** to enable or disable this dataset and set its polling interval (60 seconds by default).
