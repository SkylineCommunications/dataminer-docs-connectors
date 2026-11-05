---
uid: Connector_help_GatesAir_Intraplex_Ascent
---

# GatesAir Intraplex Ascent

The GatesAir Intraplex Ascent is a sophisticated broadcast solution designed to provide reliable, scalable, and secure audio over IP (AoIP) transport. It enables broadcasters to manage multiple audio streams efficiently and ensures high-quality, low-latency transmission. The system supports various audio codecs and network redundancy features, making it ideal for mission-critical broadcasting applications.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware                                        |
|-----------|-----------------------------------------------------------|
| 1.0.0.x   | -                                                         |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *161*

SNMP Settings:

- **Get community string**: *public*
- **Set community string**: *private*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The element created with this connector has the following data pages:

- **General**: Displays tables with all the information about **Channels** and their current configurations.

- **Stream Module**: A few tables are found here with information about **Streams** and their properties.

- **Network**: Displays config information for both **Network Access and Forwarding**.
