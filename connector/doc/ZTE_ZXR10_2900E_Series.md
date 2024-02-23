---
uid: Connector_help_ZTE_ZXR10_2900E_Series
---

# ZTE ZXR10 2900E Series

This connector is used to collect, parse, and present SNMP data sourced from the Ethernet Switch ZXR10 2928E.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version.|-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |V2.05.12B27P08         |


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


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The driver contains the following pages:

- **General**: Displays the device's system information.
- **Interface**:Displays the Interface and Interface X SNMP tables of the device.
- **Interface Rates**:Offers Rate Calculations for the Interface tables and presents a processed version of the Interfaces table.
- **IP**:Displays the IP Address, IP Route as well as the IP Net to Media tables.
- **Bridge**:Displays the Bridge address and ports as well as the Stp Protocol specifications and priority.
- **Group Management**: Allows the user to view and configure certain group management parameters. This page also has the subpages:		
   -    **Neighbor Discovery**: Displays the Dp parameters as well as the Dp Port and Trunk tables.
   -    **Topology**: Displays the Topology parameters as well as the Topology Port and Trunk tables.