---
uid: Connector_help_Ericsson_SAU-IP
---

# Ericsson SAU-IP

This connector monitors the Ericsson Service Access Unit (SAU).

## About

### Key Features

- **Monitoring of connected devices**: The connector discovers the devices and modules connected to the main Ericsson SAU and provides detailed information for each part.
- **Inputs and outputs alarm configuration**: Input and output alarm settings can be changed directly from the connector, including port configuration, alarm severity, and the specific name of the monitored port.
- **Alarm monitoring**: Alarms are collected in DataMiner and easily monitored from the Alarm Console.

## Use Cases

### Input and Output Alarm Configuration

**Challenge**: Alarm monitoring can be complex on the Ericsson SAU as its configuration is very versatile.

**Solution**: The connector allows you to supply detailed information about each configurable setting and how it affects the subsequent alarming. You can change the name of an alarm to provide more specific details about the issue, set the default configuration of the alarm to either *Normally Closed* or *Normally Opened* for different purposes, and set the severity from a dropdown menu, all on one page.

**Benefit**: Simple, straightforward way to configure alarming.

### Source of Monitored Physical Entities

**Challenge**: The monitored physical entities are available in a generic Physical Entities table from the MIB. Although the devices are on different hierarchical levels (parent and child relationship), they are stored on the same table, making it confusing to track the entire hierarchy.

**Solution**: The connector automatically traces the hierarchy of each monitored physical entity and prefixes the hierarchy to the entity, making it clear which parent component it is connected to.

**Benefit**: Reduce the need to manually trace physical entity hierarchy.

## Prerequisites

- **DataMiner version 10.2 or higher** is required.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Ericsson_SAU-IP_Technical).

