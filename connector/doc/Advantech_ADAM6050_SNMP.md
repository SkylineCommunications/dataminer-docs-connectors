---
uid: Connector_help_Advantech_ADAM6050_SNMP
---

# Advantech ADAM6050 SNMP

The Advantech ADAM6050 SNMP connector enables monitoring and management of digital and analog inputs and outputs from Advantech ADAM6050 devices. By leveraging SNMP, the connector provides real-time data access, facilitating efficient monitoring and control within the DataMiner platform.

## About

### Version Info

| Range       | Features                                             | Based on | System Impact |
|-------------|------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | <ul><li>Initial version</li></ul> | - | None |

### Product Info

| Range       | Supported Firmware |
|-------------|---------------------|
| 1.0.0.x     | -              |

### System Info

| Range       | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-------------|-----------------|---------------------|-------------------|----------------------|
| 1.0.0.x     | No              | Yes                 | -                | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMP connection to communicate with the Advantech ADAM6050 device. During element creation, configure the following SNMP settings:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Get community string**: Community string for reading device values (default: *public*).
- **Set community string**: Community string for writing values to the device (default: *private*).

### Initialization

No additional configuration of parameters is necessary upon element creation.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is accessible when the client machine has network access to the device.

## How to use

Upon creation and configuration, the connector enables real-time monitoring and control of input and output values for the Advantech ADAM6050 device. It retrieves device data over SNMP and displays it in DataMiner, allowing operators to manage device statuses effectively.
