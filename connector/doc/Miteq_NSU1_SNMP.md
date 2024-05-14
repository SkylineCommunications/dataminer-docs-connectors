---
uid: Connector_help_Miteq_NSU1_SNMP
---

# Miteq NSU1 SNMP

This is a New Switchover Unit (NSU) redundant switchover system with a fixed 1:1 configuration. This means that one backup unit is present for one primary unit. Other models can have other (non-)fixed configurations (e.g. NSU2 = 1:2 and NSUN = 1:1 to 1:12). If a primary unit fails, the backup unit will take over, on the condition that **Redundancy Mode** is set to *Automatic*.

This connector can be used as a remote control for the Miteq NSU1 device and also monitors the device.

> [!NOTE]
> This version of the connector is obsolete and should no longer be used. Instead, use range 2.0.0.x of the [Miteq NSU1](xref:Connector_help_Miteq_NSU1) connector, which uses an SNMP connection.

## About

### Version Info

| Range              | Features                                | Based on | System Impact |
|--------------------|-----------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version for SNMP communication. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 3.003              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the device.
- **IP port**: The IP port of the device.
- **Bus address**: The bus address of the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page allows you to check and modify the Unit Name.

### Converter

On this page, the **Converter Table** shows the available converters in the redundancy chain. The NSU1 has a fixed configuration that always has one primary unit and one backup unit.

The **Chain Position in Standby Mode** shows which unit in the chain is placed in standby. In a normal setup, the value for this parameter is *Backup Converter*; however, if a primary unit fails, the backup converter takes its place, and the parameter value becomes *Primary Unit*.

### System

This page shows the system's **IP**, **Gateway**, and **Subnet Mask**. These parameters can be configured.

Click the **Clock Settings** page button to view and configure the **Internal Calendar/Clock**.

The **Redundancy Mode** can be set to *Manual* or *Automatic*. In normal circumstances, it is set to *Automatic*. The *Manual* mode is mainly used for offline testing and maintenance. **Local/Remote Mode** makes it possible to switch between *Local Control* or *Remote Control*.

The **Fault Status** page button shows a summary of the statuses of the **Power Supplies**, **Converter**, and **Switch Module**.

### Logging

To retrieve the values for the **Event Log Table**, **Logging Status**, and **Number of Expected Entries**, click the **Get Logging** button.

Click the **Clear Logging** button to clear the logging on the device and the parameters on this page.
