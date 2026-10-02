---
uid: Connector_help_Raritan_Xerus_Platform_technical
description: "Monitor Raritan Xerus devices in DataMiner, including PDU power, environmental sensors, transfer switches, reliability data, and server reachability."
---

# Raritan Xerus Platform

## About

The **Raritan Xerus Platform** connector uses **SNMP** to monitor and manage Raritan Power Distribution Units (PDUs) and related rack controllers. It gives full visibility into the configuration and operating state of a device's inlets, outlets, overcurrent protectors, external sensors, and transfer switches, and lets you change their configuration where supported.

The connector supports the following Raritan device types:

- SRC
- PX4
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

### Prerequisites

- **SNMP access** to the Raritan device is needed, with the get and set community strings configured on the device matching those used by the connector.

### Connection

This connector uses an SNMP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the device.
- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## DataMiner Connectivity Framework

The **1.0.1.x** range of the Smartgrid PDU General connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Dynamic interfaces

Physical dynamic interfaces:

- Outlets: Outlet table type **out**.
- Inlets: Inlet table type **in**.
