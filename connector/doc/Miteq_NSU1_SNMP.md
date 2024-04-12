---
uid: Connector_help_Miteq_NSU1_SNMP
---

# Miteq NSU1 SNMP

This is a New Switchover Unit (NSU) Redundant Switchover System with a fixed 1:1 configuration. This means that 1 backup unit is present for 1 primary unit. Other models could have other (non-)fixed configurations (e.g. NSU2 = 1:2 and NSUN = 1:1 to 1:12).

If a primary unit fails, the backup unit will take over, on the condition that **Redundancy Mode** is set to Automatic.

## About
The connector can be used as a remote control for the **Miteq NSU1** device, and also monitors the device.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version for SNMP communication.         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |3.003         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:


- **IP address/host**: The polling IP or URL of the device.
- **IP port**: The IP port of the device.
- **Bus address**: The bus address of the device. 


### Initialization

No extra initialization is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General
This page displays the Units Name. Unit Name can be modified.

### Converter
On this page, the **Converter Table** shows the available converters in the redundancy chain. The NSU1 has a fixed configuration that always has 1 primary unit and 1 backup unit.

The **Chain Position in Standby Mode** shows which unit in the chain is placed in standby. In a normal setup, the value for this parameter is Backup Converter; however, if a primary unit fails, the backup converter takes its place, and the parameter value becomes primary unit.

### System
This page shows the system's **IP**, **Gateway** and **Subnet Mask**. These parameters can be configured.

Click the **Clock Settings** page button to view and configure the **Internal Calendar/Clock**.

The **Redundancy Mode** can be set to *Manual* or *Automatic*. In normal circumstances it is set to *Automatic*. The *Manual* mode is mainly used for offline testing and maintenance. **Local/Remote** Mode makes it possible to switch between Local Control or Remote Control.

The page button **Fault Status** shows a summary of the statuses of the **Power Supplies**, **Converter** and **Switch Module**.

### Logging

To retrieve the values for the **Event Log Table**, **Logging Status** and the **Number of Expected Entries**, click the Get Logging button.

The logging on the device and the parameters on this page will be cleared if you click the **Clear Logging** button.

