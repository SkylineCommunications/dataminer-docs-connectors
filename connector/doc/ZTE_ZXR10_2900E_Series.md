---
uid: Connector_help_ZTE_ZXR10_2900E_Series
---

# ZTE ZXR10 2900E Series

This connector is used to collect, parse, and display SNMP data from the Ethernet Switch ZXR10 2928E.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | V2.05.12B27P08     |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays the device's system information.

- **Interface**: Displays the Interface and Interface X SNMP tables.

- **Interface Rates**: Allows you to set the rate calculation method for the interface tables (*Fast* or *Accurate*) and displays a processed version of the Interfaces table.

- **IP**: Displays the IP Address Table, IP Route Table, and the IP Net to Media Table.

- **Bridge**: Displays the bridge address and ports as well as the STP protocol specifications and priority.

- **Group Management**: Allows you to view and configure certain group management parameters.

  This page also has subpages:

  - **Neighbor Discovery**: Displays the DP parameters as well as the DP Port and Trunk tables.

  - **Topology**: Displays the Topology parameters as well as the Topology Port and Trunk tables.
