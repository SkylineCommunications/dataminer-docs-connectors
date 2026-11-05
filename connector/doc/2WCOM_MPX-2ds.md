---
uid: Connector_help_2WCOM_MPX-2ds
---

# 2WCOM MPX-2ds

The MPX-2ds is a two-channel decoder designed for MPX distribution via satellite or IP.

The 2WCOM MPX-2ds connector's main purpose is to monitor the two channels of the decoder.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.24               |

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

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## Available Data Pages

- **General**: Includes information on the status of the device, including some general information.

- **Services**: Displays the available services as entries in the table **Services Info**, each representing a decoder channel. Information about each decoder channel will be displayed here.

- **Virtual Tables** subpage: Displays virtual tables, which contain information that is used to build the **Service Info** table on the Services page. The **Virtual Common Audio Decoder Input Sources Ts Demux** table shows which SAT tuner each service uses by displaying "RF1" or "RF2" in the StrInfo column. This affects the **RF Level**, **C/N**, and **TS Sync** values of the **Services Info** table.

- **Audio Sources**: Contains information and settings for the device's audio sources. At present, RTP is the only available audio source.

- **Settings**: Shows the available settings. Currently, you can configure the SNMP trap destinations and XLR channel routing.

- **Polling Config**: Allows you to configure which polling groups should be polled. By default, they are all disabled.

- **Web Interface**: The device's web interface, which is only accessible when the client machine has network access to the device.
