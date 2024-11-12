---
uid: Connector_help_ABB_Newave_UPS
---

# ABB Newave UPS

The connector allows for monitoring and configuration of the **ABB Newave UPS** through the USHA+ interface, which obtains the status from a UPS and issues commands to it.
USHA+ supports HTTP and SNMP protocols, and in this connector SNMP protocol is used.

## About

The **ABB Newave UPS** operates in the **SNMP** protocol.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

No additional configuration of parameters is necessary in a newly created element.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page contains general information about the UPS, such as the name, manufacturer, model etc..

### UPS Unit Summary

This page contains the information about the UPS battery, such as **Battery Status**, **Battery Runtime Remaining**, **Battery Temperature**, etc..
This page also contains three sub-pages **UPS Battery**, **UPS output** and **UPS Input**

### UPS Global Configuration

This page allows for various configurations to be set on the UPS, such as setting the **UPS Input voltage**, **UPS Input Frequency**, etc..

### Global UPS Shutdown Control

On this page the shutdown settings can be configured, **UPS Shutdown Type**, **UPS Shutdown After Delay**, **UPS Auto Restart**, etc..

### UPS Battery Test

This page shows the battery test information, such as **UPS Test Results Summary**, **UPS Test Start Time**, **UPS Test Elapsed Time**, etc..

### UPS Bypass

Shows **UPS Bypass Frequency**, **UPS Bypass Table**, and **UPS Bypass Number of Lines**.

### Global Alarm Table

This page shows number of alarms present, and a table with additional details for the each alarm

### Web Interface

The Web Interface