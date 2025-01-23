---
uid: Connector_help_Calix_NMS
---

# Calix NMS

Calix NMS is a variant of Calix AXOS, which is a software-defined networking (SDN) platform designed for telecommunications networks. This variant allows the monitoring of sensor telemetry for modules such as fan, voltage, current, and temperatures, as well as both Ethernet and PON interfaces.

## Configuration

### Connections

#### HTTP Connection - 0

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *18443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When the element has been created, go to the **Authentication** page to provide the username and password to poll the available devices, and then go to the **Device Settings** page to select for which devices information should be polled.

## How to use

On the **Authentication** page, provide the credentials necessary for login.

The **Device Settings** page lists all available devices and allows you to select for which ones information should be polled.

The **ONT Configuration** page displays information about the ports of each device.

The **System** page contains multiple tables displaying general information about the system, the devices, and the disk usage.

The **Readings** page has four tables displaying information about the temperature, voltage, current, and fan values, respectively.

The **Interfaces** page displays two tables with information about the Ethernet ports and PON ports, respectively
