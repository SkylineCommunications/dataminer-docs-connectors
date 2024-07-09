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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

On the **Polling Config** page, you can configure which polling groups should be polled. By default, they are all disabled.

The **Virtual Common Audio Decoder Input Sources Ts Demux** table identifies which SAT Tuner each service uses by the StrInfo value containing RF1 or RF2. This impacts the **RF Level**, **C/N**, and **TS Sync** values of the **Service Info** table.
