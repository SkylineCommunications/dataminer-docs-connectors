---
uid: Connector_help_Ramiaudio_AUF600_Technical
---

# Ramiaudio AUF600

The AUF600 is a digital audio mixer capable of handling cross-fading of three sources in AES/EBU format.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V6.5                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Polling Manager

This page contains a polling table, which displays the polling state, interval, and last polled time, and contains a **Poll** button that can be used to manually trigger the polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Contains general device information and settings.
- **Channel Status**: Contains channel status information and general channel settings.
- **Channel Error Trame**: Contains information on the error frames for each channel.
- **Channel Settings**: Contains core channel settings.
- **CSS Core Setting**: Contains core device settings.
- **Trap Configurations**: Contains SNMP trap and trap destination settings.