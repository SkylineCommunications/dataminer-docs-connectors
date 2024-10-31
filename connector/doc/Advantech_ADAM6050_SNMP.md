---
uid: Connector_help_Advantech_ADAM6050_SNMP
---

# Advantech ADAM6050 SNMP

The Advantech ADAM6050 SNMP connector enables monitoring and management of digital and analog inputs and outputs from Advantech ADAM6050 devices. By leveraging SNMP, the connector provides real-time data access, facilitating efficient monitoring and control within the DataMiner platform.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

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

### Web Interface

The web interface is accessible when the client machine has network access to the device.

## How to use

When an element has been created with this connector, you will be able to monitor and control input and output values for the Advantech ADAM6050 device in real time. The connector will retrieve device data over SNMP and display it in DataMiner, allowing you to manage device statuses effectively.
