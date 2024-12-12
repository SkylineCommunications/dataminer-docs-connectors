---
uid: Connector_help_Calix_NMS
---

# Calix NMS

Calix NMS is a variant of Calix AXOS, which is a software-defined networking (SDN) platform designed for telecommunications networks. This variant allows the monitoring of sensor telemetry for modules such as fan, voltage, current and temperatures, as well as both ethernet and PON interfaces.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version.         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection - 0

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *18443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

After the creation of the element, the user must provide the username and password to poll the available devices and after that, in the Device Settings page, select for which devices information will be polled.

## How to use

On the **Authentication** page, provide the credentials necessary for login.

The **Device Settings** page contains all availble devices and allows the user to select which ones information should be polled for.

The **ONT Configuration** page displays information about the ports each device has.

The **System** page contains multiple tables displaying general information about the system, the devices and the disk usage.

The **Readings** page has four tables displaying information about the temperature, voltage, current and fan values respectively.

The **Interfaces** page displays two tables with information about the Ethernet ports and PON ports respectively
