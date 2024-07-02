---
uid: Connector_help_Raritan_Xerus_Platform
---

# Raritan Xerus Platform

The Raritan Xerus Platform connector facilitates the monitoring and control of the following Raritan device types:

- SRC
- PX3
- PX2
- PXC
- PX0
- BCM2
- PX3TS
- SmartLock
- DX2 SmartSensors
- AMS2

> [!NOTE]
> The Xerus MIB implements all Raritan product types. This connector is therefore a generic connector that supports all these devices. Depending on the type of device you connect to, some tables may be empty.

## About

This connector uses **SNMP** to extract all relevant information concerning the configuration and operating configuration of Raritan's PDU.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 4.1.1.5-49961          |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## Usage

### Unit

This page displays information regarding the hardware configuration and the operating state of the sensors of the connected PDU units.

### Inlets

This page displays the specifications of each inlet. It also shows the current operating configuration, and it allows you to change the configuration of each inlet sensor.

### Over Current Protector

This page displays the specifications of each overcurrent protector. It also shows the current operating configuration, and it allows you to change the configuration of each sensor.

### Outlets

This page displays the specifications of all the outlets of the device. It also shows the current operating configuration, and it allows you to change the configuration.

### External Sensors

This page displays the specifications of the external sensors. It also shows the current operating configuration, and it allows you to change the configuration of each sensor.

### Server Reachability

This page lists the servers connected to the device, their respective IPs, and whether or not they can be reached.

### Transfer Switch

This page displays the transfers switches of the device. It also shows the current operating configuration, and it allows you to change the configuration.

### Control

On this page, you can control the operation of the connected elements of this device.

### Measurements Unit/Inlet/Over Current Protector/Outlet/External Sensor/Transfer Switch

These pages show the availability and values for each unit sensor, inlet, overcurrent protector, etc.

### Log Unit/Inlet/Over Current Protector/Outlet/External Sensor/Transfer Switch

These pages log the information for the relevant sensor in a span of two hours. One entity is added to the table corresponding to each minute, so there will be 120 entries per sensor.

For each sensor, the state, maximum, minimum and average value are logged. There is also an indication of whether the logged information is available.

### Reliability Data

This page contains a list of PDU reliability data entries.

### Reliability Error Log

This page contains a list of PDU reliability error log entries.
