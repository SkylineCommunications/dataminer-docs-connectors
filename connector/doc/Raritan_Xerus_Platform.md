---
uid: Connector_help_Raritan_Xerus_Platform
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

## Key Features

- **Power and environmental monitoring**: Track real-time values and status for inlets, outlets, overcurrent protectors, and external sensors.

- **Configuration control**: Change the operating configuration of inlet, outlet, overcurrent protector, and external sensor entries directly from DataMiner.

- **Transfer switch management**: Monitor and configure the transfer switches of the connected device.

- **Historical sensor logging**: Automatically log the state, maximum, minimum, and average value for every sensor, with 120 entries covering the last two hours.

- **Reliability tracking**: Collect PDU reliability data and error log entries to support proactive maintenance.

- **Server reachability monitoring**: Track which servers connected to the device are reachable, and from which IP address.

## Use Cases

### Centralized PDU Monitoring Across a Diverse Raritan Fleet

**Challenge**: Data centers and broadcast facilities often run a mix of Raritan PDU models (PX2, PX3, PXC, BCM2, and others), making it hard to monitor power and environmental data consistently across the fleet.

**Solution**: Because the connector is built on the generic Xerus MIB, a single connector type can be used to monitor any supported Raritan device, presenting the same structured pages regardless of the underlying model.

**Benefit**: Simplified fleet management and a consistent monitoring experience, without needing a separate connector per PDU model.

### Early Detection of Power and Environmental Issues

**Challenge**: Power anomalies or sensor faults on a PDU can go unnoticed until they cause downstream equipment failures.

**Solution**: The connector continuously polls inlet, outlet, overcurrent protector, and external sensor values, and keeps a two-hour rolling log of state, minimum, maximum, and average values per sensor.

**Benefit**: Operators can spot abnormal trends quickly and act before a fault escalates into an outage.

### Proactive Maintenance Through Reliability Data

**Challenge**: Identifying recurring hardware issues on a PDU typically requires manually querying the device or reviewing vendor tools.

**Solution**: The connector exposes the device's reliability data and error log entries directly in DataMiner.

**Benefit**: Maintenance teams can review PDU health history alongside all other monitored equipment, in one place.

## Technical Reference

### Prerequisites

- **SNMP access** to the Raritan device is needed, with the get and set community strings configured on the device matching those used by the connector.

### Connection

This connector uses an SNMP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the device.
- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).
