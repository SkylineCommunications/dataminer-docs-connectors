---
uid: Connector_help_ZTE_ZXR10_Technical
---

# ZTE ZXR10

The **ZTE ZXR10 connector** enables monitoring and management of multiple models within the ZXR10 series. These devices are used in data center environments and support high-density interfaces, low latency, and features such as VXLAN, SDN, MC-LAG, and Virtual Switch Clustering.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.1.x [SLC Main] | Initial version | - | - |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |  V5.00.00R6P99                    |

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

## How to use

This connector is intended to be used as a monitoring platform that allows you to check the status of the interfaces, the fans status reported, the power supplies info, and the temperature of the corresponding modules within the system.

The General page contains general information about the device and also has a Polling Control subpage where you can activate/deactivate the polling of some tables if necessary.
