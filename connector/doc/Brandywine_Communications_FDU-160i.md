---
uid: Connector_help_Brandywine_Communications_FDU-160i
---

# Brandywine Communications FDU-160i

The function of this protocol is to monitor and set different variables on the Brandywine FDU-160i device using SNMP.  The FDU-160i is a signal distribution amplifier that is contained in a compact 1u rack-mount chassis.  The system accepts two of frequency inputs (typically 10MHz).
It provides automatic changover if one of the on-line source inputs fail, and each input is capable of driving all sixteen outputs.  Manual source select override is available on the front panel or throough the Ethernet interface.  User control of the unit is via a built in web browser with graphical interface or directly through the protocol via SNMP.
Applications available on the FDU-160i include secure communications systems, satellite ground stations, digital television broadcasting and any system requiring highly reliable frequency outputs.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |   Initial Version    |-         |-         |

### Product Info


|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-       |



### System Info


|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

No additional configuration of parameters is necessary.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

General
The General page contains information about the device i.e. Serial Number, Product Name, Version, and Location.

Refrence and Inputs
This page multiple read/write snmp params that show different editable configurations for refrence data and input data including threshholds and volt unit selection.

Output Status
This page displays status' for output data

Output Config
This page allows the configuration of different output ports 1-16, as well as their alarm threshholds.

Traps
This is where your traps are configured on a table

Offsets
This page allows the user to configure Offsets based on time and units.

Configuration
The configuration page allows the configuration of Ip addresses as well as displaying their current values.

 

