---
uid: Connector_help_Snell_Wilcox_IQVDA01
---

# Snell Wilcox IQVDA01

The **Snell Wilcox IQVDA01** is an analog video distribution amplifier. This connector is using the SNMP protocol to monitor and configure the device.
## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |5.1..6         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device. (default: *public*)
- **Set community string**: The community string used when setting values on the device. (default: *private*)

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

You can find all the information you need to monitor the amplifier on the General and Video pages.