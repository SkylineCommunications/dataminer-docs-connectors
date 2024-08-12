---
uid: Connector_help_2WCOM_MPX-2c
---

# 2WCOM MPX-2c

The MPX-2c is a point-to-point or point-to-multipoint MPX codec using IP-based network technologies for real-time distribution of complete FM-MPX (FM composite signal) to connect the signal generation in the studio directly to the transmitter site.

## About

### Version Info

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.19                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- The **General** page displays the system information.
- The **Monitoring** page displays the monitoring tables.
- The **Services** page displays the list of services available in the device and their alarm status.
- On the **Polling** page, you can define the polling groups frequency.
