---
uid: Connector_help_Megatec_NetAgent9
---

# Megatec NetAgent9

Comprehensive UPS management device with flexible configuration via Web Browser, NMS, Telnet, or SNMP. The NetAgent9 supports the MegaTec Single and Three Phase UPS protocols.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Feature1</li><li>Feature2</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |2.9.2.r1.588         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMPv2) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element mainly displays SNMP parameters as defined in the device MIB.

The *Alarms* page contains an Alarms table which displays SNMP traps forwarded by the connected device. The resolved status is dependent on whether a previous alarm with the same description was captured in Dataminer.
Alarms can be deleted through the table context menu.
