---
uid: Connector_help_Vertex_BRK-1201
---

# Vertex BRK-1201

This connector uses serial communication to retrieve information from the **Vertex BRK-1201** device and allow the end user to control and monitor the switches.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.x                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device, e.g. 10.11.12.13.
- **IP port**: The port of the connected device.
- **Bus address**: The bus address of the connected device.

## How to use

On the **General** page, you will find general information about the device together with some general monitoring and config data.

The **Configuration** page displays the configuration parameters of the device.

The **Alarms** page lists the currently active and latched alarms on the device.
