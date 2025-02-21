---
uid: Connector_help_Ericsson_SAU-IP
---

# Ericsson SAU-IP

This connector monitors the Ericsson Service Access Unit (SAU).

## About

### Key Features

- **Monitoring of Connected Devices**: The connector discovers the devices and modules connected to the main Ericsson SAU and provides detailed information of each part.
- **Inputs and Outputs Alarm Configuration**: Input and Output alarm settings can be changed directly from the connector, including; port configuration, alarm severity and specific name of the monitored port.
- **Alarm Monitoring**: Alarms are collected on DataMiner and easily monitored from the alarm console.

## Use Cases

### Input and Output Alarm Configuration

**Challenge**: Alarm monitoring can be complex on the **Ericsson SAU** as configuration is very versatile.

**Solution**: The connector supports the user by supplying detailed information of each configurable setting and how they affect the subsequent alarming.
Name of the alarm can be changed to provide more specific details of the issue, default configuration of the alarm can be set to either Normally Closed or Normally Opened for different purposes, and severity can be set from a dropdown menu all on one page.

**Benefit**: Simple, straightforward way to configure alarming.

### Source of Monitored Physical Entities

**Challenge**: The monitored physical entities are available on a generic Physical Entities table from the MIB. Although the devices are on different hierarchical levels (parent and child relationship), they are stored on the same table making it confusing to track the entire hierarchy.

**Solution**: The connector automatically traces the hierarchy of monitored physical entity and prefixes the hierarchy to the entity, making it clear which parent component it is connected to.

**Benefit**: Reduce the need to manually trace physical entity hierarchy.

## Prerequisites

- **DataMiner version 10.2 or higher** is required.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Ericsson_SAU-IP_Technical).
