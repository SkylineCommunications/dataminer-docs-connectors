---
uid: Connector_help_GeoSync_Microwave_1+2_RCU_LNB_Series
---
# GeoSync Microwave 1+2 RCU LNB Series

## About

The **GeoSync Microwave 1+2 RCU LNB Series** connector enables seamless integration of 1+2 Low-Noise Block downconverter (LNB) redundancy systems with **DataMiner**, ensuring optimal performance and reliability in satellite communication infrastructures. Designed to support both manual and automatic switching, the connector facilitates **real-time monitoring and control via SNMP**, offering robust visibility into device status, signal paths, and power configurations.

It provides operators with access to a wide range of **operational parameters**, such as signal strength and lock status, along with **switch positions** and **redundancy configurations**, including priority settings and failover status. This integration empowers broadcasters and satellite operators to proactively manage their infrastructure, reduce downtime, and streamline operations from a centralized, user-friendly interface.

## Key Features

- **Full SNMP monitoring**: Polls all SNMP-compliant parameters.
- **Manual and auto switching control**: Allows remote switching between LNB inputs and supports automatic priority logic.
- **Redundancy-aware monitoring**: Displays current active path and associated priority settings.
- **Web interface compatibility**: Supports device-level diagnostics via a built-in web interface.
- **LNB power control**: Allows users to control all power-related settings on the device.
- **DataMiner DCF-ready**: Integrates directly into the DataMiner Connectivity Framework for advanced use cases.

## Use Cases

### Use Case 1

**Challenge**: Ensuring uninterrupted satellite signal reception in critical broadcast environments.

**Solution**: Automatically switches between primary and backup LNBs in the event of failure.

**Benefit**: Prevents signal loss and maintains broadcast uptime without manual intervention.

### Use Case 2

**Challenge**: Manual switchovers are time-consuming and prone to errors during maintenance.

**Solution**: Allows remote switching of LNB inputs via SNMP control from the DataMiner UI.

**Benefit**: Reduces operational risk and enables rapid reconfiguration from anywhere.

### Use Case 3

**Challenge**: Lack of centralized visibility into remote LNB devices.

**Solution**: Consolidates LNB device monitoring into a single-pane-of-glass within DataMiner.

**Benefit**: Enhances operational awareness and streamlines fault detection across multiple remote sites.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_GeoSync_Microwave_1_2_RCU_LNB_Series_Technical).
