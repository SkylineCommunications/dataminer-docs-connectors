---
uid: Connector_help_Vertex_BRK-1201
---

# Vertex BRK-1201

The **Vertex BRK-1201** connector will display information related to the **Vertex BRK-1201** device.

## About

The connector has a serial communication to the device and allows the end user to control and monitor the switches.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |1.x        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

  - **IP address/host**: The polling IP of the device e.g. 10.11.12.13.
  - **IP port**: The port of the connected device.
  - **Bus address**: The bus address of the connected device.

### Initialization

No additional configuration of parameters is necessary in a newly created element.

## How to use

### General Page

This page contains general information about the device together with some general monitoring and config data.

### Configuration Page

This page displays the configuration parameters of the device.

### Alarms Page

This page contains the currently active and latched alarms on the device.
