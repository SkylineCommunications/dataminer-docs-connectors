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
> The Xerus MIB implements all Raritan Product types. Therefor this connector is a generic connector type that supports all these devices.  
> Dependant on the type, some tables might be empty.

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

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

## Usage

### Unit

In this page can be found information regarding the hardware configuration and the state of operation of the sensors of the connected PDU(s) unit(s).

### Inlets

In this page can be found the specifications of each inlet. It also shows the current operating configuration and the options allowing changes to said configuration of each inlet sensor.

### Over Current Protector

In this page can be found the specifications of each Over Current Protector. It also shows the current operating configuration and the options allowing changes to said configuration of each sensor.

### Outlets

In this page can be found the specifications of all the outlets of the device. It also shows the current operating configuration and the options allowing changes to said configuration.

### External Sensors

In this page can be found the specifications of external sensors. It also shows the current operating configuration and the options allowing changes to said configuration of each sensor.

### Server Reachability

In this page are listed the servers connected to the device, their respective IPs and whether or not they are reachable.

### Transfer Switch

In this page are identified the transfers switches of the device. It also shows the current operating configuration and the options allowing changes to said configuration.

### Control

The Control Page presents the options allowing to control the operation of the connected elements of this device.

### Measurements Unit

This page shows the availability of and the values of each Unit sensor.

### Measurements Inlet

This page shows the availability of and the values of each Inlet sensor.

### Measurements Over Current Protector

This page shows the availability of and the values of each Over Current Protector sensor.

### Measurements Outlet

This page shows the availability of and the values of each Outlet sensors.

### Measurements External Sensor

This page shows the availability of and the values of each External sensor.

### Measurements Transfer Switch

This page shows the availability of and the values of each Transfer Switch sensor.

### Log Unit

This page logs the Unit sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Log Inlet

This page logs the Inlet sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Log Over Current Protector

This page logs the Over Current Protector sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Log Outlet

This page logs the Outlet sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Log External Sensor

This page logs the External sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Log Transfer Switch

This page logs the Transfer Switch sensor information in a span of 2 hours. One entity is added to the table corresponding to each minute, therefore there will be 120 entries per sensor.

For each sensor it is logged the state, maximum, minimum and average value. There is also an indication whether the logged information is available.

### Reliability Data

This page contains a list of PDU reliability data entries.

### Reliability Error Log

This page contains a list of PDU reliability ErrorLog entries.
