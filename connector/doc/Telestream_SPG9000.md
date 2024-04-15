---
uid: Connector_help_Telestream_SPG9000
---

# Telestream SPG9000

Timing and reference system.

The Telestream SPG9000 Timing and Reference System elevates IP/Hybrid Timing through Dual Independent PTP Sources and Enhanced Satellite Connectivity. It offers two autonomous 1G/10G IP ports for Precision Time Protocol (PTP) sources and reference timing derived from worldwide GNSS standards, guaranteeing video synchronization in hybrid SDI/IP and IP-centric setups.

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

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]
- **Bus address**: [The bus address of the device. (default: *byPassProxy*)]

SNMPv3 Settings:

- **Username**: [The SNMPv3 username.]
- **Security level**: [The SNMPv3 security level.]
- **Authentication type**: [The SNMPv3 authentication type.]
- **Authentication password**: [The SNMPv3 authentication password. (default: *public*)]
- **Privacy type**: [The SNMPv3 privacy type.]
- **Privacy password**: [The SNMPv3 privacy password. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General Information

This page displays 2 sections:

#### System Info

- *System Name*
- *System Contact*
- *System Location*
- *System Uptime*

#### Health Status

- *Reference Status*
- *Time Status*
- *PTP 1 Grandmaster Status*
- *PTP 2 Grandmaster Status*
- *Hardware Status*
- *Power Supply 1 Status*
- *Power Supply 2 Status*
