---
uid: Connector_help_Moxa_ioLogik_E1212
---

# Moxa ioLogik E1212

The Moxa ioLogik E1212 retrieves I/O data and supports application connectivity.

This connector retrieves information from the device via SNMP. It displays basic information about the device, as well as the status of the existing DI channels. For each DI channel, some settings can also be configured.

## About

### Version Info

| Range              | Key Features     | Based on    | System Impact    |
|--------------------|------------------|-------------|------------------|
| 1.0.0.x [SLC Main] | Initial version  | -           | -                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Displays general parameters such as server model, system up time, and firmware version.
- **Digital I/O**: On this page, you can find the **DI channel monitor table** and **DIO channel monitor table**. **DI Channel monitor table** allows you to monitor all available digital input channels, whereas **DIO channel monitor table** allows you to monitor all available digital input/output channels. Both table allows you to set waveform related parameters for each channel such as mode, filter, trigger and counter, and also configure a custom name for each channel.
