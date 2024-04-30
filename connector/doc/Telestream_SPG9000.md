---
uid: Connector_help_Telestream_SPG9000
---

# Telestream SPG9000

The Telestream SPG9000 timing and reference system elevates IP/hybrid timing through dual independent PTP sources and enhanced satellite connectivity. It provides two autonomous 1G/10G IP ports for Precision Time Protocol (PTP) sources and reference timing derived from worldwide GNSS standards, allowing video synchronization in hybrid SDI/IP and IP-centric setups.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2.0.2              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).
- **Bus address**: The bus address of the device (default: *byPassProxy*).

SNMPv3 Settings:

- **Username**: The SNMPv3 username.
- **Security level**: The SNMPv3 security level.
- **Authentication type**: The SNMPv3 authentication type.
- **Authentication password**: The SNMPv3 authentication password (default: *public*).
- **Privacy type**: The SNMPv3 privacy type.
- **Privacy password**: The SNMPv3 privacy password (default: *private*).

#### HTTP Connection

This connector uses a secondary HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *80*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the **General Information** page, you can find system info and health status info.

The system info includes the System Name, Contact, Location, and Uptime.

The health status info includes the Reference Status, Time Status, and Hardware Status, as well as PTP grandmaster and power supply status information.

The **System Health** page gives an overview of all detailed PSU, Fan, Temperatures and Voltage readings and statuses.
