---
uid: Connector_help_Sencore_SDI2X
---

# Sencore SDI2X

This connector is used to monitor the **Sencore SDI2X** device. This device supports both SDI-to-IP and IP-to-SDI workflows. It also supports SMPTE 2022-6 and TR-03/SMPTE 2110. The user can configure the direction (SDI to IP or IP to SDI) for each channel independently. The platform supports one or more channels, which can be configured to convert SDI video inputs into IP output streams, or IP input streams into SDI video outputs. It will encapsulate or de-encapsulate the SDI video according to SMPTE 2022-6 standard. The platform also supports redundancy using the SMPTE 2022-7 seamless switching standard.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.2.3              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: Default:*161*.

SNMP Settings:

- **Get community string**: Default: *public-community.*
- **Set community string**: Default: *private-community.*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector contains the following data pages:

- **General**: Contains general status and information parameters. Below this page, you can find the **Network**, **Date/Time**, **SNMP** and **Syslog** subpages, which contain status and configuration parameters.

- **Channels**: Contains settings related to each different channel along with the inputs and outputs.

- **Input**/**Output**: These pages contain the other input- or output-related configuration parameters, which are not related to a specific channel.

- **Alarms**: Contains the **Alarms** and **Events Log** tables.
